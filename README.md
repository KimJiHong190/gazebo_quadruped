# gazebo_quadruped

This repository provides the necessary tools to create a controller package for the GO1 robot using ROS2 within the Gazebo simulation environment. It simplifies the process of integrating the GO1 robot into Gazebo and setting up ROS2 control, specifically using `effort_controller`.

![go1_example](https://github.com/user-attachments/assets/bd71f60e-a17e-445c-8213-87c32b73d519)


## Features
- **Controller Package Creation**: Easily create a controller package for the GO1 robot.
- **Pre-configured Simulation and Control**: Integration of the GO1 robot into Gazebo and the setup of ROS2 control are already completed.
- **Custom Controller Development**: Develop your own controllers in the `quadruped_controller` package.
- **Efficient Setup**: Quickly set up the Gazebo world and ROS2 control in ROS2.

## Repository Structure
- **go1_description**: Contains URDF files for the GO1 robot. Replace these files with different URDFs to use other robots.
- **go1_gazebo**: Includes a config file with the ROS2 controller YAML file. Modify the PID and other settings in this file. Currently, it uses `effort_controllers/JointGroupEffortController`.
- **quadruped_controller**: Write the controller for the robot here. You need to specify effort values for each joint.

### Example Controller Code
```python
self.joint_effort_publisher = self.create_publisher(Float64MultiArray, '/joint_effort_controller/commands', 10)

def publish_joint_effort(self):
    msg = Float64MultiArray()
    msg.data = [float(pos) for pos in self.torques[0]]
    self.joint_effort_publisher.publish(msg)
```

## Installation and Running

Ensure you have ROS2 Humble installed and follow these steps:
```terminal
git clone https://github.com/KimJiHong190/gazebo_quadruped.git
cd gazebo_quadruped
colcon build --symlink-install
source install/setup.bash
ros2 launch go1_gazebo go1_gazebo.launch.py
```

## Issues
If you encounter any issues while using this package, please feel free to report them.
