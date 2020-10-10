# ROS Navigation Tutorial Directory #

This directory provides the necessary packages needed to complete the [Navigation tutorial](https://github.com/UTRA-ART/Caffeine/wiki/Navigation-Fundamentals) for UTRA ART's ROS sub-team.

One is expected to implement the missing *functionality* to get the robot contained in this directory to navigate autonomously. The primary focus is to set up and understand `robot_localization` and the `navigation` stack!

**Note:** this directory is derived from the [SumoROS](https://github.com/erickmu1/SumoROS) repository written by [Erick Mejia Uzeda](https://github.com/erickmu1) to transition UTRA SUMO to ROS to enable building sumo bots entirely in simulation.

## Overview of Packages ##

### /description ###

Contains the code needed to simulate the sumo bot. A robot is built using URDF and the model (+ properties) from CAD. There are also launch files which serve to launch Gazebo and spawn the robot.

The provided robot (model of Tesla's cybertruck) is already complete and should work as is. One is not expected to modify the robot itself!

> **Note.** I did not create the meshes for the cybertruck model we are using! I forgot to keep a reference to the creator but I want to acknowledge their due credit nonetheless.

### /odom ###

This package does not currently exist - you will create it. Here you will use `robot_localization` to fuse sensor readings from:
- encoders
- imu

This will produce a fused, more stable odometry reading. The nodes `robot_localization` has also allows publishing the much needed `odom` frame.

For those who are a bit more ambitious, the next step would consist of adding a GPS plugin and using the `navsat_transform` node + `ekf_localization` node to pubilsh the `map` frame!

### /nav_stack ###

This package also... does not exist. To create it, you will use the navigation stack. By identifying and connecting the appropriate parts of your pre-built robot (found in `/description`) and your more stable odometry readings to the navigation stack. The end goal: the robot will navigate autonomously given a goal.

To test it out, you would specify a nav goal, which is very easily done in RViz.

---

You will notice that there are quite a few parameters to define when using `robot_localization` and the navigation stack. Developing a good understanding of the robot you are given and the purpose of these packages will help you complete this tutorial!

> **Note.** Your goal is not to build a robot in simulation, but it is still necessary to understand the code which describes the robot and its sensors.
