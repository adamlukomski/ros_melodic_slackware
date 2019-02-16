# ros_melodic_slackware
Packages sketch for ROS Melodic on Slackware 14.2

http://barelywalking.com/?p=483

Before using - read all the warnings and disclaimers, this is quite highly experimental and risky.

# Usage

In short?

I assume you have a working sbotools (you have done at least once "sbosnap fetch")
Packages qt5 and PyQt5 will take a LOT of time to compile, consider installing them first on your own (for example from AlienBob repository)

```
git clone https://github.com/adamlukomski/ros_melodic_slackware
sboconfig -o ros_melodic_slackware/
sboinstall ros-melodic-slackware
```

One of the possible queques: (I already had qt5)
docutils setuptools-scm python-dateutil python-empy python-catkin_pkg PyYAML python-rosdistro python-rospkg python-rosdep python-vcstools python-wstool python-rosinstall python-rosinstall_generator libxkbcommon libwacom ninja meson python-evdev pyudev libinput python2-sip enum34 numpy3 defusedxml netifaces PyOpenGL pycrypto python-gnupg pydot apache-log4cxx ros-melodic-desktop



# Loose notes

This script will compile a ROS Melodic with some slight patches.

The files will get downloaded to /tmp/SBo/ros-melodic-desktop-20190214, the build_isolated and devel_isolated will be there.
By default the script uses wget to fetch everything from github in accordance with .rosinstall, wstool can be manually turned on.
The install dir during the compilation is /tmp/SBo/package-ros-melodic-desktop, so it in theory should not conflict with the existing ROS builds in /opt/ros.
The package after installation places ROS in /opt/ros/melodic.

It is lib64-compatible, but there is still a "ln -s lib64 lib" workaround present - plugins.xml still have hardcoded links to lib/, sorry.

The ros-melodic-desktop downloads as a primary DOWNLOAD a semi-dummy package from github.com/ros/ros, that is not used later on, for the sake of compatibility.


# DISCLAIMER

Usage of ANYTHING and EVERYTHING in here is risky. I'm constantly testing it on my production system, two qemu virtual machines (x86 and x64), and a robotics laboratory at work, but I do not guarantee anything. 

As far as I know, when I started publishing my results on building ROS on Slackware on 19/09/2016, there were no other successful tutorials for it (really, the google results pages had like two results from 2011), so everything I've ever done and shown here is pretty much improvised by me. Since then I've seen on google at least one more page detailing Slackware build and a ROS wiki page dedicated to it - I have not read nor verified those results and don't intend to, because I simply don't have enough time. So this is purely my interpretation of how those packages could look like - you have been warned. Why? Because I tried really hard to be as Slackware-esque about installing ROS as I possibly could, to my knowledge. I didn't get even half of the stuff right, but I try. And if this way of thinking actually conflicts with the ROSs way of thinking, sorry about that.
