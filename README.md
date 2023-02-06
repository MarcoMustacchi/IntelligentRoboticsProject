## Usage

To build the package see [build](#build).

To use the package you have to

- start the gazebo simulation:
  ```bash
  roslaunch tiago_iaslab_simulation start_simulation.launch world_name:=ias_lab_room_full
  ```
- start the navigation stack:
  ```bash
  roslaunch tiago_iaslab_simulation navigation.launch
  ```
-  wait until TIAGO has tucked its arm
-  start the package:
  ```bash
  roslaunch tiago_iaslab_simulation move_scan.launch target:="float_x float_y float_yaw" [corridor:=true]
  ```

The values must be given in the `map` frame and the positions of the obstacles are returned with respect to the `base_laser_link`
frame. The program displays the markers of positions of the obstacles in RViz (in the `visualization_marker` topic).

Example:
```bash
roslaunch tiago_iaslab_simulation move_scan.launch target:="11 -0.5 -1.52" corridor:=true
```

## Build

You can use `catkin`:
```bash
catkin build tiago_iaslab_simulation
```
