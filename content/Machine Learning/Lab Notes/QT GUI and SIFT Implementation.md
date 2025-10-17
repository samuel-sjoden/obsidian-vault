## Setting Up The GUI
For this lab I decided to try to run things on my local Ubuntu distro just because I am more comfortable with my terminal here and my neovim setup works properly.

I went to [the qt designer site](https://www.pythonguis.com/installation/install-qt-designer-standalone/) and it told me to do this apt command to get the qt designer application.

```
$ sudo apt-get install qttools5-dev-tools
```

I then opened the application through my app library to open an interface that looks like this

![[Pasted image 20250929170605.png]]
I then created a new main window and added a pushbutton to turn the video feed on and off and another to get a new reference image.

I then went though and reassigned the object names to match this table:

| Widget description | Widget name       | Widget text          |
| ------------------ | ----------------- | -------------------- |
| Left button        | browse_button     | &Browse template ... |
| Right button       | toggle_cam_button | &Enable camera       |
| Left label         | template_label    | (unchanged)          |
| Right label        | live_image_label  | (unchanged)          |
The ampersand out front of the text appears to underline the first letter of the sentence. I'm not confident on what it does. Reading the sentence below the lab guide specifies that it allows for a keyboard shortcut. (i.e. hitting E enables the camera)

After renaming the window to SIFT_DEMO, I then saved the .ui in the ~/SIFT_app folder.

### Building The App

First I made a python file and made it executable in my sift project directory.
```
$ cd ~/SIFT_app
$ touch SIFT_app.py
$ chmod 700 SIFT_app.py
```

then I pasted the code provided in the lab guide into the python file
```
#!/usr/bin/env python3
from PyQt5 import QtCore, QtGui, QtWidgets
from python_qt_binding import loadUi
import cv2
import sys

class My_App(QtWidgets.QMainWindow):

def __init__(self):
super(My_App, self).__init__()
loadUi("./SIFT_app.ui", self)

if __name__ == "__main__":
app = QtWidgets.QApplication(sys.argv)
myApp = My_App()
myApp.show()
sys.exit(app.exec_())
```

The first line is the Shebang which tells the shell to start the script at this line and then passes it to the python3 environment to be executed as a script.

Then a series of imports follows. I am familiar with the cv2 library and have seen the sys package used before for interacting with the system running the script.

The rest of the file is an object, and creates the object if it is executed in its own namespace. One thing I am not sure about is the super call. I don't know why that is there.

To run the app, I called this command:
```
$ python3 SIFT_app.py
```

At first I got import errors for opencv, so I tried uninstalling and reinstalling with conda, but that did not fix the issue. I tried the following pip command, and my issues were fixed.

```
$ pip install opencv-python
```

My next issues was that the app was having issues loading the plugin
```
qt.qpa.plugin: Could not load the Qt platform plugin "xcb" in "/home/samuel/miniconda3/lib/python3.13/site-packages/cv2/qt/plugins" even though it was found.
This application failed to start because no Qt platform plugin could be initialized. Reinstalling the application may fix this problem.
```

I am going to try reinstalling once, if it doesn't work, I will save my current work by pushing it to git, and switch to the Xubuntu distro where the qt has already been set up. 

After reinstalling, the same issue occurred, so I will be making a git and switching to the pre-setup distro..

Switching to the distro was smooth and worked on the first try.

I then added the SLOT code which receives the buttons (the producer) SIGNAL to open a file window to select an image to add to the Window


#### Integrating Webcam Stream

The lab then walked me through installing a utility manager for the webcam and provided some code to integrate the webcam feed to the GUI.

The code provides some member variables about the webcams parameters. It sets the id of the camera to 0, which matched the output of what I saw when I called 
```
v4l2-ctl --list-devices
```
It then sets the frame rate of the feed to be 2, I think this is because this image processioning is fairly computationally expensive.

It then registers a callback function (a SLOT) to the signal of the connect webcam button created in the GUI. A pair of booleans are used to record the state of the camera internally
To process the video, a cv2.VideoCapture object is created. Some parameters are then set which I believe are the frame size. 

Instead of a rolling video, it looks like a timer is used to create a signal which connects to a callback function which reads from the camera. This explains why the frame rate was previously set as a constant because it will determine the There also appears to be a conversion function where the image starts as a cv image, but is then converted so that the Qt gui can handle it.

>All of the members that are producing signals are qt objects. I wonder if it is possible for me to create my own producer.


### Implementing SIFT Algorithm

I started by watching a few of the [review videos](https://www.youtube.com/watch?v=U0wqePj4Mx0) on [[Sift Object Identification]] and then a brief video on [[RANSAC]]. 

> [!Question]
>  When we are identifying keypoints in the image, we are applying a filter of a LoG. By 'applying a LoG' as a filter are we treating the LoG as a kernel and convolving the image with it? So when we say bigger LoG it just means $\sigma$ is getting bigger?
>  

The sift algorithm has already been implemented for me as an openCV function. I can use 
```
sift.detectAndCompute(ssddsds,dsdssd)
```
to get two arrays. The first one being the keypoints, and the second one, the descriptors. The descriptors are the histograms of the gradient where each element is a direction and its value is its magnitude.

The next step is to be able to identify good matches. This is where techniques like RANSAC will come in handy. When building the homography, I need to be able to fit the best model with many outliers present from bad matches.

Another alternative hat the lab guide provided which seemed fairly interesting was the FLANN matching technique. When matching keypoints for sift, the $L_{2}$ distance between the descriptor vectors are used. After the euclidean distance between all keypoints has been identified, the ratio of the two lowest (closest matches ) is found. For the point to be considered an unambiguous match, the highest match should be much closer than the second closest, so the ratio of $\frac{d_{2}}{d_{1}}$ should be small. A threshold for this ratio is set and only matches that have a ratio lower are selected.

Once the closest matches have been found, the RANSAC technique will help further eliminate outliers when creating the Homography. I dont have good intutition as to what a homography is, so I asked chat to explain it to me.



My key misunderstanding was that it was a simple linear mapping, but this is incorrect since the homography can still map to tilted images. Chat explained it in an interesting way where it described it as linear in a higher dimension where the scales and shears can be achieved. Then all of the 2D points are represented as a pair of coordinates and a third scaling factor which also gets transformed.

Using the following resources, i then put together the following implementation which successfully worked for my Mr.Bean cartoon guy.

**For the homography [cv link](https://docs.opencv.org/3.4/d1/de0/tutorial_py_feature_homography.html)**
**For the FLANN Matching [cv link](https://docs.opencv.org/3.4/d5/d6f/tutorial_feature_flann_matcher.html)**
**Using SIFT Feature Identifier [cv link](https://docs.opencv.org/3.4/da/df5/tutorial_py_sift_intro.html)** 

The bounding box worked well when the image was close and visible. It struggled to detect the image at a distance. Increasing the brightness of my phone additionally improved the detection.

If I was to improve one thing, it would be the speed that it operates. The 2 frame per second frame is painfully slow and the time required to carry out all of the operations can also be very time consuming. I increased the frame rate to 60 fps and it remained just as functional.
image
Another thing I noted was that the homography deteriorated when the image was brought to sharp angles. The matching algorithm was still finding 'good matches', but the transform would jitter. I couldn't quite capture it with the screenshot.


I experimented with another image with a bit more symmetry in it to see if it would perform any worse,
but it surprisingly handled it well.

I also tried it with myself. It didn't work.
