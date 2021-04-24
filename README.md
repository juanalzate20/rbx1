# RBX1
# Introduction
In this project the communication between the rbx1 package and the ROS environment will be made through the same topic using the remap function in the rbx1 launch to let the robot control by keyboard.
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
