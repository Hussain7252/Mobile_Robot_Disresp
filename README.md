
## Final Project Mobile Robotics : Autonomous Disaster Response & Reconnaissance using TurtleBot 3

### Summary

Developed a system using using TurtleBot 3 fitted with 360-degree LIDAR and Rasberry Pi camera v2 to autonomously navigate, map as well as detect and register April Tag position and orientation in the map frame. Cartographer_ROS is used for SLAM and the motion planning is achieved by integrating explore_liteand a custom wall follower algorithm to better navigate the environment that was setup. Other nodes were created to transform the april tag position from camera frame to map frame and register it on the map being generated by cartographer as well as a node was programmed to convert the occupancy grid map generated by cartographer to the one interpretable by explore_lite. Move_base was used to generate commands to drive the robot around.

The TurtleBot must generate a comprehensive map of the area while also identifying and cataloguing all the AprilTags present, including their unique ID numbers and absolute poses relative to the generated map.

![Video](https://www.youtube.com/watch?v=8zB-3f00F3s&t=4s)

The resulting system generated a comprehensive map of the area while also identifying and cataloguing all the AprilTags present, including their unique ID numbers and absolute poses relative to the generated map.

### Use requriment.txt for instaling the necessary pkgs and dependencies

### To run my Code

1. Open terminal and establish an SSH connection between the robot and the host PC:
    * `ssh ubuntu@IP_ADDRESS_OF_RASPI_ON_ROBOT`
- Update the `.bashrc` with the IP addresses of both devices. On the robot, the following two lines should be in the `.bashrc`
    * `export ROS_MASTER_URI=http://IP_ADDRESS_OF_REMOTE_PC:11311`
    * `export ROS_HOSTNAME=IP_ADDRESS_OF_RASPI_ON_ROBOT`
- While the following two lines should be in the `.bashrc` of the host PC:
    * `export ROS_MASTER_URI=http://IP_ADDRESS_OF_REMOTE_PC:11311`
    * `export ROS_HOSTNAME=IP_ADDRESS_OF_REMOTE_PC`
- Run turtlebot bringup on the robot.
    * `roslaunch turtlebot3_bringup turtlebot3_robot.launch`

2. Run `roscore` on the host PC in another terminal

3. Run master.launch file to start the robot.
    * `roslaunch bebop_tag_slam master.launch`
- The list of tags' global poses is automatically saved to your working directory under the filename tags\_DATETIME.txt
