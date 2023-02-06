## Usage

To build the package see [build](#markdown-header-build_1).

To use the package you have to

- start the gazebo simulation:
  ```bash
  roslaunch tiago_iaslab_simulation start_simulation.launch world_name:=ias_lab_room_full_tables
  ```
- start the apriltag stack:
  ```bash
  roslaunch tiago_iaslab_simulation apriltag.launch
- start the navigation stack:
  ```bash
  roslaunch tiago_iaslab_simulation navigation.launch
  ```
-  wait until TIAGO has tucked its arm
-  start the package:
  ```bash
  roslaunch tiago_iaslab_simulation pick_place.launch  [corridor:=true]
  ```

## Build

You can use `catkin`:
```bash
catkin build tiago_iaslab_simulation
```
