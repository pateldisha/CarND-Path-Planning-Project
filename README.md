# CarND-Path-Planning-Project
Self-Driving Car Engineer Nanodegree Program

### Goals

In this project our goal is to safely navigate around a virtual highway with other traffic that is driving +-10 MPH of the 50 MPH speed limit. We are provided the car's localization and sensor fusion data, there is also a sparse map list of waypoints around the highway. The car should try to go as close as possible to the 50 MPH speed limit, which means passing slower traffic when possible, note that other cars will try to change lanes too. The car should avoid hitting other cars at all cost as well as driving inside of the marked road lanes at all times, unless going from one lane to another. The car should be able to make one complete loop around the 6946m highway. Since the car is trying to go 50 MPH, it should take a little over 5 minutes to complete 1 loop. Also the car should not experience total acceleration over 10 m/s^2 and jerk that is greater than 10 m/s^3.

### Model Documentation
The car is able to drive at least 4.32 miles without incident..
The car drives according to the speed limit. 
Max Acceleration and Jerk are not Exceeded.
Car does not have collisions.
The car is able to change lanes.

We generate new way points from the current position of the car using the frenet coordinates. We use the current frenet coordinate of the car and extrapolate the path for next 90 meters.

#### Prediction

Here, we need to predict using the sensor fusion data. We need to know if there is a car in front of us , may be we can change lane or reduce speed. Also if there is a car to the right or left while we are changing the lane to know whether it is safe to do so.
We consider it as dangerous when the distance of the other car and our car is less than 30 meters. 

#### Behavior 

Based on the prediction, we can implement the behavior accordingly. Like where we need to speed up or slow down. It will increase or decrease the speed, also make the lane change if it is required and also if its safe. This way it will try to avoid the collision. 

#### Trajectory

Here we will calculate for the trajectory using the speed, behavior, car coordinates. 
For less calculation we transform coordinates to local car coordinates. For more continuity on the trajectory, the pass trajectory points are copied to the new trajectory. The remaining points are calculated by the spline.
The speed is changed based on the behavior and it will increase or decrease the speed on every trajectory points.
