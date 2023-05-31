# Tutlebot Simulations Aruco Map
Es el paquete de ```turtlebot3_gazebo```, pero con el mapa de manchester que ya tiene el turtlebot y los arucos precargados.
- Mapa con los arucos: ```turtlebot3_puzzlebot_world_aruco.launch```.
- Launch File: ```turtlebot3_manchester_world_aruco.world```.

## Instalar modelos
- Para que esto funcione, tienes que poner la capeta ```models``` dentro de ```$HOME/.gazebo/```
## Lanzar el mundo
```
roslaunch turtlebot3_gazebo turtlebot3_puzzlebot_world_aruco.launch 

```
# Detección de Arucos y Pose Estimation
Se utilizo el paquete de ROS desarollado por [UbiquityRobotics](https://github.com/UbiquityRobotics/fiducials/tree/noetic-devel) para la detección de arucos y la estimación de la pose.
Se modifico el launch file del paquete ```aruco_detect``` (```aruco_detect.launch```) para que sirviera con los tópicos del turtlebot3 y nuestro mundo con arucos. Para lanzar el entorno de pose estimation, es necesario incorporar el paquete ```fiducials``` en el workspace del turtlebot (junto con nuestra versión modificada de ```turtlebot3_gazebo```) y correr los siguientes launch files:
```
roslaunch turtlebot3_gazebo turtlebot3_puzzlebot_world_aruco.launch
roslaunch aruco_detect aruco_detect.launch
roslaunch fiducial_slam fiducial_slam.launch
rosrun robot_state_publisher robot_state_publisher
```
De manera adicional, se puede lanzar el rviz de ```fiducials``` para monitorear el comportamiento del sistema:
```
roslaunch fiducial_slam fiducial_rviz.launch
```
## Obtener la pose
Se puede obtener la pose con un subscriptor al tópico ```/fiducial_pose```.
```
root@5b57e27a2f2c:/ros_ws# rostopic type /fiducial_pose
geometry_msgs/PoseWithCovarianceStamped
```