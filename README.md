# RBX1

# Introduction
In this project the communication between the rbx1 package and the ROS environment will be made, through the same topic, using the remap function in the rbx1.launch  file to let the robot control by keyboard.

# Install RBX1 repository
In a terminal, first go to your <catkin_ws> source folder. Write:
```
cd ~/<catkin_ws>/src
```
Then, copy the RBX1 repository from author's github:
```
git clone https://github.com/pirobot/rbx1.git
```
Or you can install directly from ROS repository:
```
sudo apt-get install ros-<distro>-rbx1
```
if you get any trouble, try installing ROS dependencies:
```
sudo apt-get install python-rosinstall
```
# Remap
```
<remap from="/cmd_vel" to="/turtle1/cmd_vel"/>
```
```
<launch>
  <param name="/use_sim_time" value="false" />

  <!-- Load the URDF/Xacro model of our robot -->
  <arg name="urdf_file" default="$(find xacro)/xacro.py '$(find rbx1_description)/urdf/turtlebot.urdf.xacro'" />
   
  <param name="robot_description" command="$(arg urdf_file)" />
    
  <node name="arbotix" pkg="arbotix_python" type="arbotix_driver" output="screen" clear_params="true">
      <rosparam file="$(find rbx1_bringup)/config/fake_turtlebot_arbotix.yaml" command="load" />
      <param name="sim" value="true"/>
      <remap from="/cmd_vel" to="/turtle1/cmd_vel"/>
  </node>

  <node name="robot_state_publisher" pkg="robot_state_publisher" type="state_publisher">
      <param name="publish_frequency" type="double" value="20.0" />
  </node>

</launch>
```
