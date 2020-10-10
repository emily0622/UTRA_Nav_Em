# ROS Simulation Tutorial Directory #

This directory provides the necessary packages needed to complete the [Simulation tutorial](https://github.com/UTRA-ART/Caffeine/wiki/Simulation-Fundamentals) for UTRA ART's ROS sub-team.

One is expected to implement the missing *functionality* to get the robot contained in this directory to spawn and move within a custom world. Essentially one will complete building a working robot in simulation. This is equivalent to physically building the robot the team will be using, but in software!

**Note:** this directory is derived from the [SumoROS](https://github.com/erickmu1/SumoROS) repository written by [Erick Mejia Uzeda](https://github.com/erickmu1) to transition UTRA SUMO to ROS to enable building sumo bots entirely in simulation.

## Overview of Packages ##

### /description ###

Contains the code needed to simulate the sumo bot - at least it used to. Now it's your turn to write it!

A robot is built using URDF and the model (+ properties) from CAD. In this package you are given:
- RViz config file (in `/rviz`)
- Launch file which loads in the custom RViz config (in `/launch`)
- constants and inertias which describe the robot (in `/urdf`)
- meshes for all the robot parts (in `/urdf/meshes`)

> **Note.** the meshes were saved such that "-y" is considered *forward* **but** ROS conventions state that "x" should be forward. Take this into account when building the robot, since you may end up with a robot where all the parts look rotated!

> **Note.** I did not create the meshes for the cybertruck model we are using! I forgot to keep a reference to the creator but I want to acknowledge their due credit nonetheless.

To complete the robot, you need to:
- build the robot using URDF
- publish the robot's TF tree
- launch Gazebo
- spawn the robot in Gazebo
- add the following plugins
  - motor plugin (+ ros_control) to move the robot via `cmd_vel`
  - lidar plugin so the robot can *see*
- visualize the robot + lidar scan in RViz
- load in the custom world `sumo.world`

### /worlds ###

A simple sumo ring consisting of a black circle with a radius of about 1 meter and white outside of the circle. To be able to use this world run:
```
# Make the shell script executable
chmod +x ./worlds/install_world.sh

# Run the shell script
./worlds/install_world.sh
```
> This installs the sumo_ring model (written in SDF) to the `~./gazebo/models` folder.

> The world contained in this package is called `sumo.world` which spawns the model `sumo_ring`.

For the purpose of the tutorial, this package can be left as is. Feel free to look at how to write SDF and potentially add more models to the world (or create new worlds)!
