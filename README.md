# Robot Cleaning Project: Create3_Grid_Spiral_Algo

## Overall and objective
This project focuses on creating a robot capable of cleaning a room using grid spiral patterns. By combining spiral algorithms with NAV2 navigation, the robot navigates in a spiral motion to cover the entire room efficiently.

![image](https://github.com/TienDaniel/Create3_Grid_Spiral_Algo/assets/168886746/ca18fe2e-1c62-4949-a8f5-6d6d8b3b0b5e)

## Getting Started
To get started with the project, follow these steps:

### 1.Setting up the robot
- **Create 3 Roomba**: Educational vaccum robot.
- **Raspberry Pi 4**: Single-board computer for controlling the robot and place to write codes. Recommend download Ubuntu 22.04 for this project.
- **RPLiDAR**: LiDar camera for mapping and localization tasks.
  
### 2.Installing related softwares

Follow this instructions for installation:
- [Installing ROS2](#installing-ros2)
- [Installing SLAM Toolbox](#installing-slam-toolbox)
- [Installing Navigation 2](#installing-navigation-2)

#### Installing ROS2
ROS 2, or Robot Operating System 2, is an open-source robotics middleware framework. It provides libraries and tools to help developers build robot applications. Check instruction [here](https://iroboteducation.github.io/create3_docs/setup/ubuntu2204/).

#### Installing SLAM Toolbox
Next, we need to install SLAM Stoolbox:
```bash
sudo apt install ros-humble-slam-toolbox
```

And read [here](https://github.com/iRobotEducation/create3_examples/tree/humble/create3_lidar_slam) to know how to use Lidar to scan the map.

To save the map:
```bash
mkdir <maps_directory> 
ros2 run nav2_map_server map_saver_cli -f <maps_directory>/<name_of_map> 
```

#### Installing Navigation 2
Install NAV2 package:
```bash
sudo apt install ros-humble-navigation2 ros-humble-nav2-bringup
```

Configuring DDS Implementation:
```bash
sudo apt install ros-humble-rmw-cyclonedds-cpp
```

### 3.Running the Project
Get coordinates of any waypoint from the map on RVIZ app. After that, clone the project into your directory/ work space:
```bash
   git clone https://github.com/TienDaniel/Create3_Grid_Spiral_Algo.git
   ```

Download VSCode for your computer (Rasberry pi), then go into your work space and open the code using this command below, 
```bash
   cd <your_work_space_ws>/src
   code .
   ```
Then, put waypoints' coordinates into the code like here:
![image](https://github.com/TienDaniel/Create3_Grid_Spiral_Algo/assets/168886746/8e4a8458-2219-4e32-951c-1fbf92f3ecfe)

Finally, build and source:
```bash
colcon build --symlink-install
source ~/your_work_space_ws/install/setup.bash
```

Start the robot in spiral mode to clean the room.The robot will stop and navigate to the next waypoint whenever it encounters an obstacle, repeating the spiral cleaning process until all waypoints are visited.
Go back to your work space from /src:
```bash
   cd ..
  ```
Run the robot:
```bash
   ros2 run 
  ```
### 4.Contributing
Contributions and feedback are welcome! Fork the repository, make your changes, and submit a pull request.
