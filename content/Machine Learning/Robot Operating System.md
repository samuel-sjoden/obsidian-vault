## Summary / Postmortem

### ROS Communication
Instead of polling or using interrupts, ROS uses callbacks that are called whenever the specified data is published. This uses non-blocking threads that are spun up so that it is not polling.

### Process Management 
ROS often leaves processes running when you try to kill it.

Miti says to create a shell script to automate terminating all processes. This is faster than opening htop and looking for stale processes

#### Visualization Tool
```
$ rosrun rqt_gui rqt_gui
```

