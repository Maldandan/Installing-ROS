# Installing ROS on VirtualBox
To Install ROS on our PC using VirtualBox, we will need to Install the VirtualBox and then Ubuntu.
In this case, I'm using Ubuntu 20.04 and we will be Installing ROS Noetic.

## Installing the Virtual Box

For Installing VirtualBox, use this Link: https://www.virtualbox.org/wiki/Downloads

Choose VirtualBox Platform Package and start the installation.

## Installing Ubuntu

To download the ubuntu 20.04, use the Link: https://releases.ubuntu.com/20.04/
and choose the Desktop image option.

## Running Ubuntu 20.04 on VirtualBox

Go to the VirtualBox, and click on "New", then go through creation process.
After than, before you start the new machine, go to the settings, and under the "Storage", choose "Empty" under the Controller and go to "Choose a disk File" and locate your Ubuntu Iso file.
After Starting the new Machine, ubuntu installation will start in the VirtualBox!

## Installing ROS
### Setup your sources.list
Setup your computer to accept software from packages.ros.org.
```
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
```
### Set up your keys
```
sudo apt install curl # if you haven't already installed curl
curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -
```
### Installation
First, make sure your Debian package index is up-to-date:
```
sudo apt update
```
**Now pick how much of ROS you would like to install.**
**Desktop-Full Install**: (Recommended) : Everything in Desktop plus 2D/3D simulators and 2D/3D perception packages
```
sudo apt install ros-noetic-desktop-full
```
**Desktop Install**: Everything in ROS-Base plus tools like rqt and rviz
```
sudo apt install ros-noetic-desktop
```
**ROS-Base**: (Bare Bones) ROS packaging, build, and communication libraries. No GUI tools.
```
sudo apt install ros-noetic-ros-base
```
### Environment setup
You must source this script in every bash terminal you use ROS in.
```
source /opt/ros/noetic/setup.bash
```

It can be convenient to automatically source this script every time a new shell is launched. These commands will do that for you.

**Bash**
```
echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc
source ~/.bashrc
```
**zsh**
```
echo "source /opt/ros/noetic/setup.zsh" >> ~/.zshrc
source ~/.zshrc
```

### Dependencies for building packages
Up to now you have installed what you need to run the core ROS packages. To create and manage your own ROS workspaces, there are various tools and requirements that are distributed separately. For example, [rosinstall](http://wiki.ros.org/rosinstall) is a frequently used command-line tool that enables you to easily download many source trees for ROS packages with one command.

To install this tool and other dependencies for building ROS packages, run:
```
sudo apt install python3-rosdep python3-rosinstall python3-rosinstall-generator python3-wstool build-essential
```
**Initialize rosdep**
Before you can use many ROS tools, you will need to initialize rosdep. rosdep enables you to easily install system dependencies for source you want to compile and is required to run some core components in ROS. If you have not yet installed rosdep, do so as follows.
```
sudo apt install python3-rosdep
```
With the following, you can initialize rosdep.
```
sudo rosdep init
rosdep update
```


