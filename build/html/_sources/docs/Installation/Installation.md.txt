# Installation
## Dependencies
1. [unitree_guide](https://github.com/unitreerobotics/unitree_guide)
2. [unitree_ros](https://github.com/unitreerobotics/unitree_ros)
3. [unitree_ros_to_real](https://github.com/unitreerobotics/unitree_ros_to_real)

![Switch](../../images/download_pkg.png)
<center>
<br>
<div style="color:orange; border-bottom: 0.1px solid #d9d9d9;
display: inline-block;
color: #999;
padding: 1px;">All the packages you need to prepare</div>
</center>
<br>

## CMakeLists.txt
Since our program needs to support many uncertain scenarios.
For example, both A1 robots and Go1 robots need to be supported.both compiling under ROS and compiling without relying on ROS, etc. To easily switch between these requirements, we need to rely on conditional compilation.
We can get the compiler to compile what we want with a simple setup.<br>
Next, let's see how to implement conditional compilation in CMake. The settings for CMake compilation are all in the
**unitree_guide/CMakeLists.txt** file.
Open this file and at the beginning is the file used to configure conditional compilation.
```
    set(ROBOT_TYPE Go1)        # Robot models, currently supporting Go1 and A1
    set(PLATFORM amd64)        # Program compilation platform, currently supports amd64 and arm64
    set(CATKIN_MAKE ON)        # Whether to use ROS's catkin_make, ON or OFF
    set(SIMULATION ON)         # For Gazebo simulation environment, ON or OFF
    set(REAL_ROBOT OFF)        # For real robot control, ON or OFF, must be different from the previous one
    set(DEBUG ON)              # Whether to turn on Debug debugging, ON or OFF
    set(MOVE_BASE ON)          # Whether to turn on the move_base navigation function, ON or OFF
```