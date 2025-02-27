# Trajectory Generation

## Table of Contents
1. [Overview](#overview)
2. [Trajectory Profile Modifications](#trajectory-profile-modifications)
   - [Trapezoidal to Cubic Polynomial](#trapezoidal-to-cubic-polynomial)
   - [Cubic Polynomial Trajectory](#cubic-polynomial-trajectory)
3. [Trajectory Generation](#trajectory-generation)
   - [Circular Trajectories](#circular-trajectories)
   - [Linear Trajectories](#linear-trajectories)
4. [Testing Trajectories](#testing-trajectories)
   - [Trajectory Testing](#trajectory-testing)
   - [Torque Analysis](#torque-analysis)
5. [Inverse Dynamics Operational Space Controller](#inverse-dynamics-operational-space-controller)
   - [Controller Implementation](#controller-implementation)
   - [Performance Evaluation](#performance-evaluation)
6. [How to Run the Simulation](#how-to-run-the-simulation)


## Overview
This project focuses on **trajectory planning and control** for a robotic manipulator using **ROS, KDL, and Gazebo**. It includes **trajectory profile modifications**, implementation of **cubic polynomial and trapezoidal velocity profiles**, and **trajectory generation for linear and circular paths**. Additionally, an **inverse dynamics operational space controller** was developed to enhance trajectory tracking.

## Trajectory Profile Modifications
### Trapezoidal to Cubic Polynomial
- **Modified the KDLPlanner class** to replace the trapezoidal velocity profile with a cubic polynomial.
- Implemented a function to compute position, velocity, and acceleration for the **cubic polynomial profile**.

### Cubic Polynomial Trajectory
- Defined a function that calculates the **cubic polynomial trajectory**.
- Ensured smooth transitions by imposing boundary conditions for position and velocity.
- Improved control over **trajectory smoothness and motion stability**.

## Trajectory Generation
### Circular Trajectories
- **Implemented circular trajectory planning** with parameters:
  - **Trajectory duration**
  - **Starting point**
  - **Radius**
- Calculated circular paths in the **y-z plane**.

### Linear Trajectories
- Developed functions to **generate linear trajectories** based on:
  - **Start and end positions**
  - **Cubic polynomial profile** for smooth motion.

## Testing Trajectories
### Trajectory Testing
- **Updated kdl_robot_test.cpp** to validate:
  - **Linear trajectories**
  - **Circular trajectories**
  - **Trapezoidal vs. cubic polynomial profiles**

### Torque Analysis
- Used **rqt_plot** to visualize joint torque behavior.
- Tuned **control gains (Kp, Kd)** for smooth motion.
- Saved joint torque commands to a **ROS bag file** and analyzed them in MATLAB.

## Inverse Dynamics Operational Space Controller
### Controller Implementation
- Implemented the **KDLController::idCntr function** for operational space control.
- Computed **Cartesian space errors** and control gains.
- Converted trajectory errors into **joint torques** for accurate tracking.

### Performance Evaluation
- Tested the controller along predefined trajectories.
- Plotted **joint torques** to assess controller effectiveness.
- Compared tracking accuracy between different control strategies.

## How to Run the Simulation
```bash
# Step 1: Launch Gazebo with the Robot
roslaunch iiwa_gazebo iiwa_gazebo_effort.launch

# Step 2: Run the trajectory test
rosrun kdl_ros_control kdl_robot_test /src/iiwa_stack/iiwa_description/urdf/iiwa14.urdf
```


