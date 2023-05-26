# Tutlebot Simulations Aruco Map
Es el paquete de ```turtlebot3_gazebo```, pero con el mapa de manchester que ya tiene el turtlebot y los arucos precargados.
- Mapa con los arucos: ```turtlebot3_puzzlebot_world_aruco.launch```.
- Launch File: ```turtlebot3_manchester_world_aruco.world```.
Para que esto funcione, tienes que poner la capeta ```models``` dentro de ```$HOME/.gazebo/```.
<br/>
Para lanzar el mundo de gazebo usa el comando:

```
roslaunch turtlebot3_gazebo turtlebot3_puzzlebot_world_aruco.launch 

```
