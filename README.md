<p align="center">
  <img src="https://github.com/MarcoMustacchi/MarcoMustacchi.github.io/blob/main/assets/img/icons/UniPD_logo.svg" width="150">
</p>

<h1 align="center">Intelligent Robotics - Final Project <br> UniPd</h1>

<a href="https://github.com/MarcoMustacchi/IntelligentRoboticsProject/raw/master/Assignment-1.pdf">📄Task1</a>
<a href="https://github.com/MarcoMustacchi/IntelligentRoboticsProject/raw/master/IR_Assignment1.pdf">📄Report1</a>
<br>
<a href="https://github.com/MarcoMustacchi/IntelligentRoboticsProject/raw/master/Assignment-2.pdf">📄Task2</a>
<a href="https://github.com/MarcoMustacchi/IntelligentRoboticsProject/raw/master/IR_Assignment2.pdf">📄Report2</a>

# Dependencies
<a href="https://github.com/MarcoMustacchi/IntelligentRoboticsProject/raw/master/TIAGO Tutorials - Standard Install Procedure.pdf">📄TIAGO - Standard Install Procedure</a>

**NB.** This guide has been extracted from the official Wiki available at Robots/TIAGo/Tutorials so please, if you have any problem during the following steps, please take a look also at the official documentation.

TIAGO is a service robot produced by PAL Robotics. It is essentially a humanoid robot with the kinematic model of a simple mobile manipulator (differential mobile base + 6dof anthropomorphic manipulator). At the end of this install procedure you will be able to reproduce a very complex simulation that replicates all the features and capability of the real TIAGO robot. Below the results obtained at the end of this install guide.

## Installation Steps

### 1. Create Tiago workspace (optional, remind that you have to use this workspace for the assignments):

```bash
mkdir ~/tiago_public_ws
```

### 2. Install the TIAGO packages (inside your workspace folder)

```bash
wget https://raw.githubusercontent.com/pal-robotics/tiago_tutorials/kinetic-devel/ tiago_public-melodic.rosinstall
```

```bash
ros install src /opt/ros/melodic tiago_public-melodic.rosinstall
```

```bash
rosdep install --from-paths src --ignore-src -y --rosdistro melodic --skip-keys="opencv2 opencv2-nonfreepal_laser_filters speed_limit_node sensor_to_cloud hokuyo_nodelibdw-devpython-graphitesend-pip python-statsd pal_filterspal_vo_server pal_usb_utils pal_pcl pal_pcl_points_throttle_and_filter pal_kartopal_local_joint_control camera_calibration_filespal_startup_msgs pal-orbbec-openni dummy_actuators_managerpal_local_planner gravity_compensation_controller current_limit_controllerdynamic_footprint dynamixel_cpp tf_lookup opencv3 joint_impedance_trajectory_controller cartesian_impedance_controlleromni_base_description omni_drive_controller"
```

### 3. Build the workspace

```bash
source /opt/ros/melodic/setup.bash
```

```bash
catkin build -DCATKIN_ENABLE_TESTING=0
```

```bash
source devel/setup.bash
```

### 4. Source the ROS workspace using ~/.bashrc (Recommended but not mandatory)

```bash
echo"source /opt/ros/melodic/setup.bash">> ~/.bashrc
```

```bash
echo"source ~/tiago_public_ws/devel/setup.bash">> ~/.bashrc
```

Now you can close and reopen your shell. From this moment on, your shell will be always updated and pointing to your ROS workspace.


### 5. Test your simulation

To launch the simulation of the TIAGo **Steel**, execute:

```bash
roslaunchtiago_gazebo tiago_gazebo.launch public_sim:=true robot:=steel
```

The **Titanium** version can be launched as follows:

```bash
roslaunchtiago_gazebo tiago_gazebo.launch public_sim:=true robot:=titanium
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
