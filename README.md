## Udacity - Self Driving Car Nanodegree (Term 3) - Path Planning Project
[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)

Background
---
In this project, my goal is to build a path planner that will autonomously drive a car around the track in the simulator for the project without exceeding the speed limit or collide with the other cars on the road.

Overview of Repository
---
This repository contains the following source files that I have forked from the [main repository](https://github.com/udacity/CarND-Path-Planning-Project) and subsequently modified for the MPC project:

1.  [main.cpp](https://github.com/MartinKan/CarND-Path-Planning-Project/blob/master/src/main.cpp)

Summary of the Path Planning model
---
The main.cpp class implements the path planning model using spline for path creation and some rudimentary logic code and cost functions for path planning.  

The implementation of the path creation method using spline (lines 449-564) closely resembles the code that was presented to us in the accompanying project walkthrough and is therefore not my own implementation.  This part of the code creates the trajectory of the car using spline - which is a mathematical technique for creating smooth curves that passes through a set of points on a plane - so that the car would travel smoothly and does not jerk from side to side.  The forward-looking waypoints of the map that are provided by the simulator, combined with the waypoints in the previous trajectory that was computed but not yet traversed, are used to compute the new trajectory of the car.  When computing the future trajectory of the car, the waypoints of the map are transformed into a new set of coordinates that uses the car as the reference frame to make the trajectory easier to compute.  Once the new trajectory is computed, the waypoints are transformed back into the map's coordinates that the simulator would then be able to process.

The path planning part of the code is implemented using some rudimentary logic code and cost functions (lines 352-439). In a nutshell, the path planner will first check if the car ahead is too close or not. If it is, then it will slow down and check if the adjacent lane(s) has a higher lane speed or has less traffic (these represent the cost functions). A lane change will be initiated if the target lane is faster or has less traffic than the current lane, as shown below:

![alt text](https://github.com/MartinKan/CarND-Path-Planning-Project/blob/master/images/path_planning1.gif)

Running the code
---

To run the code, first compile the code by running the following command:

	cmake .. && make

Then run the code by executing the following command:

	./path_planning