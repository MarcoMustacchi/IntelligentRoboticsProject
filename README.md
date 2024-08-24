<p align="center">
  <img src="https://github.com/MarcoMustacchi/MarcoMustacchi.github.io/blob/main/assets/img/icons/UniPD_logo.svg" width="150">
</p>

<h1 align="center">Intelligent Robotics - Final Project <br> UniPd</h1>

<a href="https://github.com/MarcoMustacchi/IntelligentRoboticsProject/raw/master/Assignment-1.pdf">📄Task1</a>
<a href="https://github.com/MarcoMustacchi/IntelligentRoboticsProject/raw/master/IR_Assignment1.pdf">📄Report1</a>
<br>
<a href="https://github.com/MarcoMustacchi/IntelligentRoboticsProject/raw/master/Assignment-2.pdf">📄Task2</a>
<a href="https://github.com/MarcoMustacchi/IntelligentRoboticsProject/raw/master/IR_Assignment2.pdf">📄Report2</a>

# Installation Guide
## Step 1: Create Workspace
```bash
mkdir -p ~/tiago_public_ws/src
```

## Step 2: Navigate to Workspace
```bash
cd ~/tiago_public_ws
```

## Step 3: Initialize the Workspace
```bash
catkin_make
```
This will create the necessary build, devel, and src directories. 
It also configures the workspace for ROS development.


## Step 4: Navigate to src folder:
```bash
cd ~/tiago_public_ws/src
```

## Step 5: Clone the Package 
```bash
git clone https://github.com/MarcoMustacchi/IntelligentRoboticsProject.git
```
This will create the "tiago_iaslab_simulation" package

# Dependencies
**NB.** This guide has been extracted from the official Wiki available at Robots/TIAGo/Tutorials so please, if you have any problem during the following steps, please take a look also at the official documentation.

TIAGO is a service robot produced by PAL Robotics. It is essentially a humanoid robot with the kinematic model of a simple mobile manipulator (differential mobile base + 6dof anthropomorphic manipulator). At the end of this install procedure you will be able to reproduce a very complex simulation that replicates all the features and capability of the real TIAGO robot. Below the results obtained at the end of this install guide.

## Installation Steps

### 1. Navigate to workspace
```bash
cd ~/tiago_public_ws
```

### 2. Install the TIAGO packages (inside your workspace folder)
```bash
wget https://raw.githubusercontent.com/pal-robotics/tiago_tutorials/noetic-devel/tiago_public-noetic.rosinstall
rosinstall src /opt/ros/noetic tiago_public-noetic.rosinstall
```

### 3. Run this command to make sure that all dependencies are installed
```bash
sudo rosdep init
rosdep update
```

### 4. Run the following to make sure that all dependencies referenced in the workspace are installed
```bash
rosdep install -y --from-paths src --ignore-src --rosdistro noetic --skip-keys "urdf_test omni_drive_controller orocos_kdl pal_filters libgazebo9-dev pal_usb_utils speed_limit_node camera_calibration_files pal_moveit_plugins pal_startup_msgs pal_local_joint_control pal_pcl_points_throttle_and_filter current_limit_controller hokuyo_node dynamixel_cpp pal_moveit_capabilities pal_pcl dynamic_footprint gravity_compensation_controller pal-orbbec-openni2 pal_loc_measure pal_map_manager ydlidar_ros_driver"
```

### 5. Build the workspace
```bash
source /opt/ros/noetic/setup.bash
catkin build -DCATKIN_ENABLE_TESTING=0 -j $(expr `nproc` / 2)
```

### 6. Source the ROS workspace using ~/.bashrc
```bash
source ~/tiago_public_ws/devel/setup.bash
```
or **(Recommended but not mandatory)**
```bash
echo "source ~/tiago_public_ws/devel/setup.bash">> ~/.bashrc
```

Now you can close and reopen your shell. 
From this moment on, your shell will be always updated and pointing to your ROS workspace.

### 7. Test your simulation
To launch the simulation of the TIAGo **Steel**, execute:
```bash
roslaunch tiago_gazebo tiago_gazebo.launch public_sim:=true robot:=steel
```

The **Titanium** version can be launched as follows:
```bash
roslaunch tiago_gazebo tiago_gazebo.launch public_sim:=true robot:=titanium
```

# Assignment 1
switch to branch <a href="https://github.com/MarcoMustacchi/IntelligentRoboticsProject/tree/assignment1">Assignment1</a>

# Assignment 2
switch to branch <a href="https://github.com/MarcoMustacchi/IntelligentRoboticsProject/tree/assignment2">Assignment2</a>

# Typical ROS Workspace Scheme
```makefile
my_ros_workspace/            # Root of the ROS workspace
├── src/                     # Source directory containing all packages and repositories
│   ├── project_repo_1/      # First project repository (could be a Git repository)
│   │   ├── package_1/       # ROS package 1 in project_repo_1
│   │   │   ├── CMakeLists.txt   # CMake build script for package_1
│   │   │   ├── package.xml      # Package manifest file for package_1
│   │   │   ├── src/             # Source code for package_1
│   │   │   ├── include/         # Header files for package_1
│   │   │   ├── launch/          # Launch files for package_1
│   │   │   ├── worlds/          # Gazebo world files for simulation environments
│   │   │   ├── action/          # ROS actions definitions
│   │   │   ├── msg/             # Custom messages for package_1
│   │   │   ├── srv/             # Custom services for package_1
│   │   │   └── scripts/         # Python scripts or other executable scripts
│   │   └── package_2/       # ROS package 2 in project_repo_1
│   │       ├── CMakeLists.txt
│   │       ├── package.xml
│   │       ├── src/
│   │       ├── include/
│   │       ├── launch/
│   │       ├── worlds/
│   │       ├── action/
│   │       ├── msg/
│   │       ├── srv/
│   │       └── scripts/
│   ├── project_repo_2/      # Second project repository (could be a Git repository)
│   │   ├── package_3/       # ROS package 3 in project_repo_2
│   │   │   ├── CMakeLists.txt
│   │   │   ├── package.xml
│   │   │   ├── src/
│   │   │   ├── include/
│   │   │   ├── launch/
│   │   │   ├── worlds/
│   │   │   ├── action/
│   │   │   ├── msg/
│   │   │   ├── srv/
│   │   │   └── scripts/
│   │   └── package_4/       # ROS package 4 in project_repo_2
│   │       ├── CMakeLists.txt
│   │       ├── package.xml
│   │       ├── src/
│   │       ├── include/
│   │       ├── launch/
│   │       ├── worlds/
│   │       ├── action/
│   │       ├── msg/
│   │       ├── srv/
│   │       └── scripts/
│   ├── CMakeLists.txt       # Top-level CMakeLists.txt for catkin (usually a symlink)
│   └── package.xml          # Optional top-level package.xml if you want a meta-package
├── build/               # Build directory (generated by catkin)
├── devel/               # Development space (contains setup files, devel environment)
├── install/             # Install space (for installing built packages)
└── logs/                # Logs from builds and runs
```
