# Udacity Practice: SLAM Gmapping
Implement a `gmapping` ROS package that is based on the Grid-based FastSLAM algorithm to map an environment.
## Prerequisite before Building  
Install packages' dependencies
```
$ cd ..
$ source devel/setup.bash
$ rosdep -i install turtlebot_gazebo
$ rosdep -i install turtlebot_teleop
$ rosdep install gmapping
```
## Build
Open a new terminal and run 
```
$ cd <Your catkin workspace>
$ catkin_make
$ source devel/setup.bash
```
## Packages
- [**turtlebot_gazebo**](https://github.com/turtlebot/turtlebot_simulator)  
To use the Gazebo world file.
- [**turtlebot_teleop**](https://github.com/turtlebot/turtlebot)  
To manually control a robot using keyboard commands.  
- [**slam_gmapping**](https://github.com/ros-perception/slam_gmapping)  
To provide SLAM capabilities.
## Running the Codes
1. Open a new terminal and run
   ```
   $ roslaunch turtlebot_gazebo turtlebot_world.launch world_file:=worlds/willowgarage.world
   ```
2. Open another terminal and launch
   ```
   $ roslaunch turtlebot_teleop keyboard_teleop.launch
   ```
3. In a new terminal, run
   ```
   $ rosrun gmapping slam_gmapping
   ```
4. In another teminal, run
   ```
   $ rosrun rviz rviz
   ```
   Edit  the rviz configuration as follows
   - Change the Fixed Frame to map
   - Keep Reference Frame as default
   - Add a robot model
   - Add a camera and select the /camera/rgb/image_raw topic
   - Add a map and select the /map topic
5. You can now map the environment by driving your robot using keyboard commands.
6. (Optional) To save a map of the environment
   ```
   $ cd /home/workspace/
   $ rosrun map_server map_saver -f myMap
   ```
   With the map_server you can load and save maps. Running map_server will generate the map.pgm and the map.yaml files.