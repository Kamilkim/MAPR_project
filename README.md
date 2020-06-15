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

Uruchomienie mapy:

$ roslaunch mapr_project mapr_project.launch

Uruchomienie mapy z rysowaniem sciezki

$ roslaunch mapr_project mapr_project_ompl.launch


# Tasks

1. Generowanie mapy - na podstawie informacji z repozytorium https://github.com/ANYbotics/grid_map zostal napisany skrypt elevMap_create.py, ktory generuje mape wysokosciowa (widoczna ponizej) o wymiarach 64x64 piksele. Mapa nastepnie zostala zapisana do rosbaga.

![Mapa](https://github.com/Kamilkim/mapr_project/blob/master/doc/elevation_map.JPG)

2. Losowanie startu i mety - skrypt subsykrybuje mape wysokosciowa z uruchomionego rosbaga i losuje na jej powierzchn dwa punkty startowy i koncowy. Zostalo dodane ogranicze ktore powoduje, ze punkty nie moga byc wylosowane blizej siebie wiecej niz na 5 pikseli. Nastepnie punkty sa publikowane w topiku.

![Mapa](https://github.com/Kamilkim/mapr_project/blob/master/doc/elevation_map_points.JPG)

3. Szukanie sciezki - do wyszukiwania sciezki zostal uzyty algotyrm RRT* z biblioteki OMPL, dodatkowo sciezka jest optymalizowana pod wzgledem kosztu, ktorym jest wysokosc na mapie w danym punktcie. Do optymalizacji kosztu uzyto rowniez elementu biblioteki OMPL - Optimization Objectives
https://ompl.kavrakilab.org/optimizationObjectivesTutorial.html. Node planera subskrybuje mape z rosbaga i losawane punkty z topika, nastepnie wyszukuje sciezke i publikuje ja w topiku.

![Mapa](https://github.com/Kamilkim/mapr_project/blob/master/doc/elevation_map_path.JPG)


4. Node z planerem jest uruchamiany co sekunde.
![Mapa](https://github.com/Kamilkim/mapr_project/blob/master/doc/planning.gif)

Punkty startowy i koncowy sa zapisywane jako zdjecie. Po znalezieniu sciezki rowniez ona zapisywana jest jako zdjecie. 

![Mapa](https://github.com/Kamilkim/mapr_project/blob/master/doc/data_point.png)
![Mapa](https://github.com/Kamilkim/mapr_project/blob/master/doc/data_path.png)



