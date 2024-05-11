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
#### Set up work space
We're using [Python](https://www.how2shout.com/linux/install-python-3-9-or-3-8-on-ubuntu-22-04-lts-jammy-jellyfish/#:~:text=Steps%20to%20install%20Python%203.9%20or%203.8%20on,...%207%207.%20Uninstall%20Python%20and%20PPA%20) and code on [VSCode](https://linuxiac.com/install-visual-studio-code-on-ubuntu-22-04/) for this project.

Create work space for your project, you can name 'my_ws' below any names that you like
```bash
mkdir my_ws
```

Then, move direction into your work space directory, 'my_ws' in this case or any name of work space that you name above
```bash
cd my_ws
```

Now, you're in your work space, clone our project by this command:
```bash
git clone https://github.com/TienDaniel/Create3_Grid_Spiral_Algo
```

After that, we will just keep the file 'src' and you can delete other irrelevant files manually or by using commands below. It will delete 'docs' folder and 'README.md' file:
```bash
rm -rf /docs
rm -r /README.md
```

Finally, build and source:
```bash
colcon build --symlink-install
source ~/my_ws/install/setup.bash
```

#### Set up waypoints
After successfully scan the room with SLAM Toolbox, you will see the map show up on RVIZ. Then using 'Publish Point' on the tool bar like image below, hovering it to any location that you want on the map and you will see the cooridinates showing up as (x,y,z) form in the bottom left corner of RVIZ. Then you can write these down on papers or somewhere, take 3 decimals after the point.
![image](https://github.com/TienDaniel/Create3_Grid_Spiral_Algo/assets/168886746/38bf9f8e-e3c4-45f3-afce-ce361b31fe28)

Now, you should save the map with command below, you should change the <name_of_map> to whatever you like:
```bash
ros2 run nav2_map_server map_saver_cli -f my_ws/ name_of_map
```

Then, go to directory 'src/my_robot_controller/my_robot_controller' to run VSCode. Again, make sure you download VSCode for your Ubuntu.
```bash
cd src/my_robot_controller/my_robot_controller
code .
```

Next step, open the python file named 'test_waypoint_spiral.py', scroll all the way down and put waypoints' coordinates into the code like here:
![image](https://github.com/TienDaniel/Create3_Grid_Spiral_Algo/assets/168886746/8e4a8458-2219-4e32-951c-1fbf92f3ecfe)

Build and source again:
```bash
colcon build --symlink-install
source ~/your_work_space_ws/install/setup.bash
```

#### Run the robot
Make sure you don't turn off the RVIZ. Because we need it to set the initial waypoint for the robot using '2D Pose Estimate' on the tool bar like image below. You need to approximately identify the position of your robot on the map by your eyes, then drag and drop the green arrow point to the direction where your robot is facing (where bumper is facing).
![2D_pose_estimate](https://github.com/TienDaniel/Create3_Grid_Spiral_Algo/assets/168886746/d29c1b6e-1172-4575-8530-deb9441df746)

Then, you run these 3 command lines below, you can check up installation in our website for these commands:
```bash
ros2 launch nav2_bringup localization_launch.py map:=<the path to your map> use_sim_time:=false
```
```bash
ros2 launch nav2_bringup navigation_launch.py use_sim_time:=false map_subscribe_transient_local:=true
```
```bash
ros2 run my_robot_controller waypoint_spiral
```

##### Our website
Every step we show above is pretty much all project. You can access to our website to look up for directions on how to run the codes and other related materials: 
[CLick here](https://tiendaniel.github.io/Create3_Grid_Spiral_Algo/)

### 4.Contributing
Contributions and feedback are welcome! Fork the repository, make your changes, and submit a pull request.
