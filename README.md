# RRT-Non-holonomic-constraints-turtlebot3
# Project - 5 | Final Project
```
Course  : ENPM661 - Planning
```
Team: 

|Name|UID|Directory ID|
|:---:|:---:|:---:|
|Krishna Hundekari|119239049|krishnah|

# Python Files
```
It is stored in the directory proj3/src/
```

# Video of the results

2D visualisation for RRT:

![ezgif com-video-to-gif (2)](https://github.com/KrishnaH96/RRT-Non-holonomic-constraints-turtlebot3/assets/113392023/3700b6ea-fce6-459c-99b3-d928f499f354)

3D visualisation in Gazebo for turtlebot3 tracing path planned by RRT:

![ezgif com-video-to-gif (3)](https://github.com/KrishnaH96/RRT-Non-holonomic-constraints-turtlebot3/assets/113392023/6e0350a6-ce64-4026-bb7d-56675478480e)


# Running the code
There are four ways of running a python script which are as follows:

 - You may run it in your operating system's terminal. For e.g., In windows - cmd.
 - Python interactive mode.
 - Integrated Development Environment (IDE) like VSC.
 - Opening the script file from folder

First check the version of python installed in your system by running following command:

*python --version*

If it yields result like this one:

*Python 3.8.10*

Then you may run script in terminal by typing following line in the directory it is located at:

*python3 proj3p2_shail_krishna.py*

# Dependencies

import following modules/library for the script to run correctly: 

*import  numpy as np*  			

*import cv2 as cv*  								

*from queue import PriorityQueue*  

*import math as math*

*from math import dist*

*import matplotlib.pyplot as plt*

*import time*  	

*import copy*

*import matplotlib.patches as patch*

*import rospy*

*from geometry_msgs.msg import Twist*

*from nav_msgs.msg import Odometry*

*from tf.transformations import euler_from_quaternion*

# Gazebo Visualization

Simulate the path planning implementation on Gazebo with the TurtleBot 3 Burger robot.

## ROS Package

Download the zip file ```proj3.zip```

ROS package folder has been included in the zip file at following path:

```
This ROS package can be directly copied to ```src``` folder of catkin_ws if it is already setup. If not, a catkin_ws needs to be setup.

Then build the catkin workspace so that it can integrate the package:

```
$ cd ~/catkin_ws && catkin_make
```

Now, as suggested everything has been wrapped in two steps i.e., gazebo initialization, turtlebot spawning to origin defined in map and moving to goal pose. This can be initiated using following two steps"

1. Step - 1

```
$ rosrun proj3 rrt_final.py 
```

In the same terminal, execute following command

2. Step - 2

```
$ roslaunch proj3 proj3.launch  
```

The above launch will run two nodes:

1. Gazebo_ros node that spawns the turtlebot so make sure turtlebot and gazebo ros packages are correctly installed in your system.
2. Python script with publisher to send commands and subscriber to get odom orientation data for reorienting the bot for reaching to goal accurately.

# User input

Note 1: Don't give the start point where all children are in the obstacle space.

Note 2: Use RPM1 as 20 and RPM2 as 40 for clean and smooth visualization.

Defining user defined following attributes in below described format:
```
Enter obstacle clearance:
```
Here user has to enter value to be bloated around obstacles [mm].

```
Note: Make sure the obstacle clearance doesn't add up to block the right end of the map since it will keep on computing childrens through action set.

All user inputs are in 'mm'.
```

```
Hey!! Where to start? Please enter home 'x' coordinate:
```
Here user has to enter value of home position's x coordinate as per new origin defined in project documentation [mm].

Similarly, user has to provide complete home pose i.e., x, y & orientation (Theta in degrees) and for goal pose i.e., just x & y to move foraward.

Next, the user will be prompted with following last two inputs:
```
Enter first possible RPM for the wheel: 
```

```
Enter second possible RPM  for the wheel: : 
```
Here wheel RPMs needs to be defined which will decide the action step in 8 different directions as follows:
```
[0, RPM1]
[RPM1, 0]
[RPM1, RPM1]
[0, RPM2]
[RPM2, 0]
[RPM2, RPM2]
[RPM1, RPM2]
[RPM2, RPM1]
```

Reasonable threshold of 100 mm for checking duplicates is defined in code for faster computation and cleaner output.

Kindly provide the input from your terminal and in the format it is explained above for correct implementation

The output visualization will be generated with shortest path backtracked.

**Sample-1**

```
User Input:

Enter obstacle clearance: 5

Hey!! Where to start? Please enter home 'x' coordinate:  
250

Please enter home 'y' coordinate: 
1800

Give home orientation:  
0

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Now give the goal 'x' coordinate 
2000

Now give the goal 'y' coordinate 
1500

Enter first possible RPM for the wheel: 
20

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Enter second possible RPM  for the wheel: 
40

```

### Terminal output

```
Time needed for the algorithm: 17.225619077682495

```



