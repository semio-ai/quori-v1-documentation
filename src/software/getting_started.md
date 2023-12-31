# Getting Started

## Running from the Robot

From a Linux PC session with Xorg:

```bash
ssh -X quori<robot number>@<robot address>
roscore &!
```

## Running from a PC

You need a [ROS 1 "noetic" installation](https://wiki.ros.org/noetic/Installation).

> Make sure to source ROS 1 before continuing:
> ```bash
> source /opt/ros/noetic/setup.bash
> ```

The `quori_ros` repository is a ROS 1 workspace, that can be built with `catkin_make`.

```bash
git clone https://github.com/Quori-Robot/quori_ros.git
cd quori_ros
git submodule init
catkin_make
. ./devel/setup.sh
```

Then run `roscore` with the appropriate `ROS_IP` and `ROS_MASTER_URI` environment variables
on both the PC and the robot.

## Starting the Demo configuration

Then you can run the demo launch file:

```bash
roslaunch quori_launch demo.launch
```

It launches:

- the navigation stack
- the mapping and the laser publishers
- the controller stack for Quori in holonomic mode

Other launch files are available in the `quori_launch` package:

- launch the laser stack (including filtration) and SLAM system.
  ```bash
  roslaunch quori_launch mapping.launch
  ```

- Publishes the laser's static transform.
  ```bash
  roslaunch quori_launch tf_base_laser.launch
  ```

- Publishes the laser filtration stack (used by mapping.launch).
  ```bash
  roslaunch quori_launch filtered_laser.launch
  ```
