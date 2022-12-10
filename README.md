Knight Bot: A mobile robot that can navigate inside workplaces


Introduction:
An autonomous mobile robot is a robot that is capable of moving and navigating independently without the need for direct human control. This type of robot can be useful for a variety of tasks, including performing inspections, delivering goods, and providing security in workplaces.
To implement such a robot, you would need to use several different components and technologies. The Raspberry Pi is a small, low-power computer that can be used to run the robot's main control software. The Arduino is a microcontroller that can be used to control the robot's motors. And the Hokuyo lidar is a laser-based rangefinder that can be used to scan the robot's surroundings and create a 2D map of its environment.
In our case, this robot will navigate inside workplaces to deliver items and documents to and from the workers.

Steps:
First, you must assemble the robot to test it while developing. Below is my robot assembly.

	
Then, we start with developing the motors controller code to control the speed and the orientation of the robot and send odometry information to the Raspberry Pi. The code is provided below.

https://drive.google.com/file/d/1s3edeRqVitiESKT_9dsqvDUkylLbM9Em/view?usp=drivesdk

On the Raspberry Pi side, we need to install the Ubuntu server and then install ROS. ROS is an open-source software platform for building and managing robotic systems. It provides a set of tools and libraries for developing robot applications, as well as a runtime environment for running and coordinating robot behaviors. The way to install Ubuntu and ROS is explained in this video:

 https://youtu.be/OIqkmgOY_Ws

After installing ROS on Raspberry Pi, we need to do the same on our laptop to be able to develop the system with more convenience. To install it follow the instructions here:

http://wiki.ros.org/noetic/Installation/Ubuntu 

After setting up our environment, we need to install "Rosserial". Rosserial is a protocol for communicating with ROS using a serial connection. It allows microcontrollers, like the ones found on Arduino boards, to communicate with ROS and take advantage of its features. The way to install is simple, just write:

sudo apt-get install ros-indigo-rosserial-arduino
sudo apt-get install ros-indigo-rosserial
To be able to control and see the data published we need to connect with the Raspberry Pi and establish an SSH connection, the way to do that is to write:

  ssh pi@”ip address” 

And Then insert the password:

Enter the password: *******
You successfully connected your laptop with Raspberry Pi. Now run roscore and run "rosserial node" to start receiving data we need:

rosrun rosserial_python serial_node.py _port:=/dev/ttyACM1 _baud:=115200

Now if we want to control the robot using the keyboard, we can install the teleop twist node:

sudo apt-get install ros-noetic-teleop-twist-keyboard 
and then run it:

rosrun teleop_twist_keyboard teleop_twist_keyboard.py 

All what you need now is just follow the instructions and you will be able to drive the robot from your keyboard.

References:

https://automaticaddison.com/how-to-set-up-the-ros-navigation-stack-on-a-robot/

https://www.youtube.com/watch?v=wfDJAYTMTdk

https://www.youtube.com/watch?v=WLVfZXxpHYI

https://www.youtube.com/watch?v=1tqYrWqrbC8&list=PLRG6WP3c31_U7TFGduEIJWVtkOw6AJjFf

