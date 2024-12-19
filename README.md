Repository for Homework 4 of Robotics Lab course made by Marco Bartone P38000237, Giacomo Caiazzo P38000236, Matteo De Simone P38000232, Nicola Monetti P38000238.

# Robotics Lab - Homework 4

### Overview
This is a report of the Homework 4 of Robotics Lab course using Docker and ROS2 with Gazebo and RVIZ2. The repo contains the steps to download the folders from github and to run the launch file for the simulations of the mobile robot "fra2mo".

### Usage

Open the terminal, open the container and enter into the directory where you want to download the folder, then download it with:

	git clone https://skibiditoilet

To build the packages, enter into the ROS2 workspace and build them with:

	colcon build

Atfer this, use the source command:

	source install/setup.bash

--------------------------------

To load the world with leonardo_race_field and the mobile robot, run the simulation on Gazebo with:

	ros2 launch rl_fra2mo_description gazebo_fra2mo.launch.py

To map the environment with SLAM (autonomous navigation included), open another terminal and use the following command:

	ros2 launch rl_fra2mo_description fra2mo_explore.launch.py

After this, open another terminal and use the following command to make the mobile robot follow a trajectory:
  
	ros2 run rl_fra2mo_description follow_waypoints.py

It's possible to select between two different paths:
-  "map_explore", to explore the map automatically, useful to save it;
-  "goals", to follow a set of points in the world map.

N.B. To save the map after the robot has explored the map successfully, use the following command in the ROS2 workspace on a different terminal:

	ros2 run nav2_map_server map_saver_cli -f map_name

--------------------------------

To make the robot follow and detect the aruco marker in the leonardo_race_field (on the left side of the prismatic yellow obstacle), use the following commands in the ROS2 workspace *in two different terminals*:

	ros2 launch rl_fra2mo_description fra2mo_aruco.launch.py
	ros2 run rl_fra2mo_description aruco_finder.py
