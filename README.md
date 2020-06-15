# mapr_project

# Dependencies:

$ sudo apt-get install ros-melodic-map-server ros-melodic-dwa-local-planner libompl-dev

$ sudo apt-get install ros-melodic-grid-map

$ pip install pathlib

# Installation

$ sudo apt-get update

$ cd ~/catkin_ws/src

$ git clone https://github.com/Kamilkim/mapr_project.git

$ cd ~/catkin_ws/

$ catkin_make_isolated

$ source devel_isolated/setup.bash

# Run example

$ roslaunch mapr_project mapr_project_ompl.launch

# Tasks

1. Generowanie mapy - na podstawie informacji z repozytorium https://github.com/ANYbotics/grid_map zostal napisany skrypt elevMap_create.py, ktory generuje mape wysokosciowa (widoczna ponizej) o wymiarach 64x64 piksele

![Mapa](https://github.com/Kamilkim/mapr_project/blob/master/doc/elevation_map.JPG)

2. in the new terminal run script 

    $ rosrun mapr_project elevMapExample.py

3. add topic "reflected_map" in rviz


