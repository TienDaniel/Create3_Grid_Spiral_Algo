# Robot Cleaning Project: Create3_Grid_Spiral_Algo

## Ideas and expected output
![image](https://github.com/TienDaniel/Create3_Grid_Spiral_Algo/assets/168886746/ca18fe2e-1c62-4949-a8f5-6d6d8b3b0b5e)

## What the Project Does
This project focuses on creating a robot capable of cleaning a room using grid spiral patterns. By combining spiral algorithms with NAV2 navigation, the robot navigates in a spiral motion to cover the entire room efficiently.

## Why the Project is Useful
The project is useful for automating the cleaning process in indoor environments. It utilizes advanced algorithms to optimize the cleaning path and ensure thorough coverage of the room.

## Getting Started
To get started with the project, follow these steps:

### 1.Installation
Clone the project repository to your local machine.
Make sure you have ROS2 and NAV2 installed.
### 2.Configuration
Mount the RPLIDAR sensor as specified in the documentation.
Set up the "slamtoolbox" for your ROS2 version.
### 3.Running the Project
Launch the robot's control software.
Drive the robot around the room to scan the map using NAV2.
Set waypoints around the map using NAV2.
Start the robot in spiral mode to clean the room.
The robot will stop and navigate to the next waypoint whenever it encounters an obstacle, repeating the spiral cleaning process until all waypoints are visited.
### 4.Customization
Adjust the parameters and algorithms as needed for specific room sizes and cleaning requirements.
### 5.Contributing
Contributions and feedback are welcome! Fork the repository, make your changes, and submit a pull request.
