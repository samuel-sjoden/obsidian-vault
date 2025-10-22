## Gym-Gazebo
OpenAI gym is a [[Reinforcement Learning]] toolkit that is integrated with the Gazebo simulator and [[Robot Operating System]]. It is used as a way to benchmark robotics.

Reinforcement learning training is now being done in simulation because of the time required and prevention of damage to hardware during the learning process. The idea is that if the robot can learn in a simulation and the simulation is accurate enough, the robot can easily translate what it learned in simulation to the real world.

### Training Models In Gym Gazebo
The  researchers outline a simple set of actions that the robot can take chosen with the purpose of maximizing the performance of the robot. They want the robot to travell in straight lines, so they make it move forward even during turns and reward forward behavior more than turning.

### Q-Learning
[[Q-Learning]] is a style of reinforcement learning training that allows the agent to learn the optimal policy to maximize reward. 
$$
Q(s_{t},a_{j}) \leftarrow Q(s_{t}, a_{j}) + \alpha \left[ r_{t+1} + \gamma \text{max}_{i}\left[ Q(s_{t+1}, a_{i}) \right] - Q(s_{t}, a_{j})\right]
$$
Q-Learning is an iterative process where each time I take an action, I recurse through this formula to update the $Q$ values for the actions taken for the previous states based on the reward gained at the current step.
- $\alpha$ (Learning Rate) determines how quickly the agent develops new habits 
- Discount Factor ($\gamma$) describes how strongly the reward at the current states propagate back to previous actions.
Another final important factor is the explore/exploitation ratio $\epsilon$ which determines how often the agent follows the perfect optimal path and how often it experiments with other strategies to get a better understanding of the reward landscape.

Each episode of training is a sequence of actions taken before a terminating action or a limit is reached. During this episode the agent will accumulate reward and explore the reward landscape. At the end of each episode, the simulation resets and the agent is returned to a start position.

## Gym-Gazebo
### Environment
A similar framework which contains a robot, a world, and training parameters. There will be a seperate directory where the reinforcement tasks instantiate an environment which then runs for some episodes.

The lab guide first took me through adding a gym-gazebo environment which has the .urdf,.world, and launch file to generate t robot and an world for the robot. 
There was a .launch file for both the robot and world. The worlds were linked to materials which had an assosiated image data.

Similar to the  [[ROS Robot Implementation]] lab, the .xacro file for the robot described the robot with a skid steering plugin and a camera at the front of the robot.

Once the environment was in, I then registered the environment with gym-gazebo. This also contained information on the max number of episodes to carry out before resetting.

For some reason I had to run the __init__ file once before the environment was properly registered and I could run the code which instansiates the training environment.

![[Pasted image 20251017153935.png]]
__Figure 1.__ Robot in the environment after being instantiated with the example code


### State Vectors and Q values
My next task is to define the state space of the agent. The state space should describe how close the robot is to the line so that being closer to the line is rewarded and further is not.

The state vector recommended is a 10-dimensional state vector where which the line is. It could be in a super position of lines, or I could choose just to use the center of the line and accept higher oscillations.

I am going to reuse my code from the previous lab here.

```
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
```
 Which was implemented to be:
 ```
 NUM_BINS = 10
state = np.zeros(NUM_BINS)
eye = np.eye(NUM_BINS)
done = False

line_center = find_center(cv_image)

if line_center is None:
self.timeout += 1
if self.timeout > 30:
done = True
else:
height, width = cv_image.shape[:2]
index = int((width - 1) / NUM_BINS * line_center)
state = eye[index]

# Label the image shown with the state vector
text = str(state)
org = (50, 100)
fontFace = cv.FONT_HERSHEY_SIMPLEX
fontScale = 1.5
color = (0, 0, 0)
thickness = 2
lineType = cv.LINE_AA
cv.putText(cv_image, text, org, fontFace, fontScale, color, thickness, lineType)

cv.imshow("raw", cv_image)
 ```

### Qlearn Functions
My next objective is to complete is to set up $4$ functions in a custom Qlearn object. The QLearn object contains its hyperparameters ($\alpha,\gamma,\epsilon$), a set of $q$, and a list of actions.

It looks like I am writing my own implementation of QLearning with the functionality to learn from a previous set of states and actions, choose an action depending on $\epsilon$ and the current optimal policy, and be able to save and load the state-action values from a pickle or csv.

#### Pickling
Pickling in python is similar to JSON objects in that it's a way to easily serialize objects. The output (pickle) files that the objects are not secure and are also not human readable.

The two key functions for pickling are *pickle.dump* which writes the serialized version of the given object to a file and *pickle.load* which returns the object that was serialized in the file. You have to open the file before you load or dump. Since its a serialized object it should be in wb (write binary) or rb (read binary).

**Resources**
[digital ocean](https://www.digitalocean.com/community/tutorials/python-pickle-example)
[python docs](https://docs.python.org/3/library/pickle.html)

>[!Question]
> Is the Q value the reward value at at given (state, action) tuple?

>[!Answer]
> The Q value is the expected total discounted reward given a state and an action

The q values are a dict! this means I input the state and action, and it gives me the q value?

>[!Question]
> How does python evaluate a loop like this?
> ```
> q_values = [q_values[i] + mag * (random.uniform(0,1) - 0.5) for i in q_values]
> ```
>  How does it avoid mutating the data as it goes?


