## Develop A Line Following Robot
For my code, I want to create a node which subscribes to the raw image data, then publishes cmd_vel.

My code will be in the node folder inside of the ros_lab project
```
$ tree
.
├── CMakeLists.txt
├── launch
│   ├── move_robot.launch
│   ├── my_launch.launch
│   └── robot.launch
├── media
│   └── materials
│       ├── scripts
│       │   └── track.material
│       └── textures
│           ├── monza.png
│           └── spa.png
├── models
│   └── track
│       ├── model.config
│       └── track.sdf
├── node
│   ├── README.txt
│   └── robot_controller.py
├── package.xml
├── README.md
├── scripts
│   └── move_robot.py
├── urdf
│   ├── macros.xacro
│   ├── materials.xacro
│   └── robot.xacro
└── worlds
    └── 353_ros_lab.world

```

I then have to make some minor adjustments to the move_robot.launch file so that it points to my robot_controller.py file.
```
<launch>

<!-- My Package launch file -->

<node pkg="enph353_ros_lab"

type="robot_controller.py"

name="move_robot"

output="screen">

</node>

</launch>
```

The  node that I want to build will subscribe to the raw image data. I will then use CV bridge to be able to use the image data. Then I will be able to use my code from the previous lab to be able to identify the center of the line. 

Once I have the center of the line, I can create an error function where it is minimised when the center of the camera is lined up with the center of the line.

Once I have an error function, I can scale the angular movements to put the robot back on the line. It will then publish the data to the cmd_vel, keeping the robot on the line.

#### CV Bridge
Looking at the CV bridge [documentation](https://wiki.ros.org/cv_bridge/Tutorials/ConvertingBetweenROSImagesAndOpenCVImagesPython), it looks like the object provided will produce Image objects. I'm not sure what they are or if openCV can handle them. 

### Subscribing To The Data
Looking at the rospy [documentation](https://wiki.ros.org/ROS/Tutorials/WritingPublisherSubscriber%28python%29) on creating subscriber nodes, rospy has a function that links a data stream to a type and callback function. The callback function is where my logic code will be.

I will need to place a rospy.spin() command somewhere so that the python does not finish execution.

To fill out the Subscriber function, I need a data type that the received data is, but i'm not sure what it is. 

A quick google search led me to the command 
```
$ rostopic info <topic - name>
```
which gave me this output which was very helpful
```
Type: sensor_msgs/Image

Publishers: 
 * /gazebo (http://skynet:43845/)

Subscribers: None
```

### Tuning The PID
Once the code was in place, with some appropriate roslog commands to see the data flow, the last step was to tune the numbers so that the robot could successfully line follow. 

```
$ rosrun rqt_image_view rqt_image_view
```
This command was helpful in viewing the output of the camera.

### Final Script and Result

```
#!/bin/env python3

import rospy

from cv_bridge import CvBridge, CvBridgeError

import cv2 as cv

from sensor_msgs.msg import Image

from geometry_msgs.msg import Twist

  

## Portion of the image (from the top) to ignore when detecting the line

START_ROW = 0.80 #: The amount of the upper half that is ignored (%)

  

## Proportional control gain for angular correction

KP = 0.005

  

## Base linear speed of the robot

BASE_SPEED = 0.1

  

##

# @class LineFollower

# @brief A ROS node class for line following using camera input.

#

# This class subscribes to the robot's camera feed, processes images to detect

# the line position, computes control commands using a proportional controller,

# and publishes velocity commands to the robot.

#

class LineFollower:

##

# @brief Constructor: initializes subscribers, publishers, and state.

#

# Subscribes to the camera topic, publishes velocity commands, and sets

# up the CvBridge for converting ROS image messages to OpenCV images.

#

def __init__(self):

rospy.Subscriber('/rrbot/camera1/image_raw', Image, self.callback)

self.pub = rospy.Publisher('/cmd_vel', Twist,queue_size=1)

self.bridge = CvBridge()

self.move = Twist()

self.linear_speed = BASE_SPEED

self.angular_speed = 0

  

##

# @brief Callback function for processing camera images.

#

# Converts ROS Image messages to OpenCV images, finds the line center,

# computes proportional control corrections, and publishes Twist commands.

#

# @param data The incoming ROS Image message.

#

def callback(self, data):

try:

cv_image = self.bridge.imgmsg_to_cv2(data)

except CvBridgeError as e:

rospy.logerr(e)

return

center = self.find_center(cv_image)

_, w = cv_image.shape[:2]

if center is None:

rospy.logwarn("Line center not found, stopping robot")

self.angular_speed = 0

self.linear_speed = 0

else:

error = (w / 2) - center

correction = KP * error

self.angular_speed = correction

self.linear_speed = BASE_SPEED

  

self.move.angular.z = self.angular_speed

self.move.linear.x = self.linear_speed

rospy.loginfo(f"The published linear speed {self.linear_speed} and angular {self.angular_speed}")

# rospy.loginfo(f"error {error} and image center {w/2}")

self.pub.publish(self.move)

##

# @brief Finds the x-coordinate of the line center in the image.

#

# Processes the bottom portion of the image, thresholds it to detect the

# line, and computes the centroid using image moments.

#

# @param frame The OpenCV image (BGR format) from the robot's camera.

# @return The x-coordinate of the line center, or None if no line is detected.

#

def find_center(self, frame):

h, _ = frame.shape[:2]

start_row = int(h * START_ROW)

bottom_region = frame[start_row:, :]

  

gray = cv.cvtColor(bottom_region, cv.COLOR_BGR2GRAY)

# Binary threshold + invert to make line = white

_, img_bin = cv.threshold(gray, 127, 255, cv.THRESH_BINARY)

img_inv = cv.bitwise_not(img_bin)

  

# Compute centroid

M = cv.moments(img_inv)

if M["m00"] != 0:

cx = int(M["m10"] / M["m00"])

rospy.loginfo(f"Line center x={cx}")

return cx

else:

rospy.logwarn("No line detected!")

return

  

##

# @brief Main entry point of the program.

#

# Initializes the ROS node, creates a LineFollower object, and enters

# the ROS spin loop.

#

def main():

rospy.init_node('robot_controller')

lf = LineFollower()

rospy.spin()

  

##

# @brief Script entry point.

#

if __name__ == '__main__':

main()
```

### Reflection
With the brief stint of testing I found some things that I immediately wanted was an easy way to restart the robot from a given position with a set orientation.

Another thing that I think would be very helpful when debugging more complex systems is a way to visualize my data. I agree that telemetry would be very useful here. With ros running I wonder if there is a way to stream plots or visualisations while the robot is running as opposed to reading print statements and debugging from there. ROS kinda forces me to use their features so it might have to be a separate node or something. Definitely something I want to look into though.