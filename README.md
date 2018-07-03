# RoboND-SLAM-Project

 This report studies Simultaneous Localization and Mapping (SLAM) problem using Real-Time Appearance-Based Mapping (RTAB-Map) in a Gazebo environment. A robot model from the previous localization project was used with an added RGB-D camera to map both predefined and custom made environment. With data from robot sensors and odometry data , using RTAB-Map ROS library database of environments were built, and both 2D and 3D maps were generated.Please refer to [project writeup](https://github.com/Zerde/RoboND-SLAM-Project/blob/master/slam-project-writeup.pdf) for more information.

## Project Setup and run

Create catkin workspace, if you haven't already.For this project catkin_ws is used, if your workspace name is different, change the commands accordingly. 

```sh
$ mkdir -p ~/catkin_ws/src
$ cd ~/catkin_ws/src
$ catkin_init_workspace
$ cd ~/catkin_ws
$ catkin_make
```
Create package called "slam_project":
```sh
$ cd ~/catkin_ws/src
$ catkin_create_pkg slam_project
```
Copy the content of this repo into slam_project folder, source and build the project:
```sh
$ cd ~/catkin_ws
$ source devel/setup.bash
$ catkin_make
```
To run the mapping process open up 4 terminals and run following commands seperately:
```sh
$ cd ~/catkin_ws
$ roslaunch slam_project world.launch
$ roslaunch slam_project teleop.launch
$ roslaunch slam_project mapping.launch
$ roslaunch slam_project rviz.launch
```
Then on the terminal that run teleop.launch move robot around the map using keyboard to map the world
![Alt text](./images/kitchen_dining.png?raw=true "Title")
![Alt text](./images/mapping-kitchen.png?raw=true "Title")

To change the world environment edit `world_name` parameter in world.launch file
```
<include file="$(find gazebo_ros)/launch/empty_world.launch">
  	<!-- <arg name="world_name" value="$(find slam_project)/worlds/kitchen_dining.world"/>-->
    <arg name="world_name" value="$(find slam_project)/worlds/myworld.world"/>
    <arg name="paused" value="$(arg paused)"/>
```

