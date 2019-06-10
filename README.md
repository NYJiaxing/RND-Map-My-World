# Udacity Robotics Nanodegree - Map My World

## The rtabmap database viewer
![](/images/rtabmapdatabaseViewer.png)

## Introduction

SLAM project of the Udacity Robot Software Engineer Nano Degree. In previouse projects, I completed building the world and the robot, create ROS nodes to control the robot following the white ball and using partical filter to localize robot itself in a pre-defined map. In this project, I completed to create a map for a unknown world with help of a laser scan sensor-LIDAR sensor and a depth sensor to simultaneously get the RGB and 3D information of the front object. The new algorithm used in this project is SLAM and RTAB-Map to create a 3D map for the robot.

## Getting Started
To view this project, you must have Gazebo and ROS Kinetic installed on Linux.

[Click here for Gazebo download and installation instructions](http://gazebosim.org).

[Click here for ROS installation instructions](http://wiki.ros.org/ROS/Installation).

To begin, several ROS packages need to be installed as dependencies (system, teleop-keyboard, rtabmap):

```
$ sudo apt-get update && sudo apt-get upgrade -y
$ sudo apt-get install ros-kinetic-teleop-twist-keyboard
$ sudo apt-get install ros-kinetic-rtabmap-ros
```

With the dependencies installed, download/clone the repository, navigate up to the root level directory, and execute:

```
$ catkin_make
$ source devel/setup.bash
$ roslaunch my_robot master_launch.launch
```

To operate the robot via the keyboard, open a second terminal, navigate to the root level directory, and execute:

```
$ source devel/setup.bash
$ rosrun teleop_twist_keyboard teleop_twist_keyboard.py
```

As you move the robot around, RTAB-Map will build a map of the room. When you terminate the mapping window, the map will be saved as a  database file in the launch folder. To view the map, open the termianl in the folder and type:

```
$ rtabmap-databaseViewer rtabmap.db
```

Click "yes" when asked about database parameters, and then select "Constraint View" and "Graph View" from the View menu.

## The problem may face

1. If download the rtabmap ROS package from its github page, the rtabmap version is 0.19.xx but in this project, we should use 0.17.xx, so this confused me a lot when configure the environment. For this project, just need the 0.17 version, to install the package, just type in the terminal
```
$ sudo apt-get install ros-kinetic-rtabmap-ros
```
2. In the first two loops of mapping, the 2D map may distort, but after map the world more than 3 or 4 times, the 2D map becomes more robust and the distortion disappear. 
