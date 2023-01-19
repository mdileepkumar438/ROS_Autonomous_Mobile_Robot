# ROS_Autonomous_Mobile_Robot

<details open="open">
  <summary>Contents</summary>
  <ol>
    <li><a href="#In-this-Repository">In This Repository</a></li>
    <li><a href="#How-to-use-this-Repository">How to use this Repository</a></li>
    <li><a href="#Workflow-of-Project">Workflow of Project</a></li>
  </ol>
</details>

## In this Repository
The robot has a URDF file with all of the essential parameters defined to load into Gazebo in the simulation and be able to move and interact with objects in the simulation to complete the goal or prove that it is possible to achieve it.
The package includes instructions for initiating the simulation for the first time. 

## How to use this Repository
* Move into your workspace/src folder
```
 cd path/to/workspace/src/
 Example: cd ~/catkin_ws/src/
```

* Clone the repository in your workspace
```
git clone https://github.com/mdileepkumar438/ROS_Autonomous_Mobile_Robot
```

* Perform make and build through catkin
 ```
 cd /path/to/workspace_root/
 ##e.g ~/catkin_ws/
 catkin_make
 ```
 
 * Source your Workspace in any terminal you open to Run files from this workspace ( which is a basic thing of ROS )
```
source /path/to/catkin-ws/devel/setup.bash
```
* To Get the Turtlebot World (Assessment World)

*Note: Make sure you have the Turtlebot3 setup done correctly.*
```
git clone https://github.com/mdileepkumar438/Assessment_world.git
```

* Launch Dolly bot (URDF file) in Gazebo world
```
roslaunch explorer_bot map.launch
```

* Above Command launches Rviz and Gazebo with all the necessary Objects.

<img width="500" alt="Screenshot 2022-10-14 at 4 01 18 PM" src="https://user-images.githubusercontent.com/102908088/213438777-b371d7b0-36e1-48b2-929e-3a1d7ac78218.png"> <img width="500" alt="Screenshot 2022-10-14 at 4 01 43 PM" src="https://user-images.githubusercontent.com/102908088/213439665-06694952-5626-40a9-bdb2-88123a0107ed.png">

* Type ``` rostopic list ``` to check the `robot_base_velocity_controller/cmd_vel` topic is published or not,

<img width="553" alt="Screenshot 2022-10-14 at 4 03 46 PM" src="https://user-images.githubusercontent.com/102908088/213442046-5119d848-8d65-43c6-9a1d-a9c981c59386.png">

* To Drive the Robot, make sure the teleop_twist_keyboard is Publishing to the above `robot_base_velocity_controller/cmd_vel` topic is-order to Drive the Bot
```
rosrun teleop_twist_keyboard teleop_twist_keyboard.py 
```
<img width="500" alt="Screenshot 2022-10-14 at 4 21 27 PM" src="https://user-images.githubusercontent.com/102908088/213441911-01b9736f-458d-44a9-8887-d80193cb76f2.png">

*If Teleop_twist_keyboard is not installed, type below command to install it*
```
sudo apt-get install ros-<noetic/melodic/..>-teleop_twist_keyboard
```


----
## Workflow of Project
- designed a personalized robot called Dolly.
The movie will cover a four wheel differential drive type that was built entirely from scratch using URDF and has joints and links.
Following the robot's development, I added Gazebo Plugins (Differential Drive and Laser Scanner) to the URDF of the robot.
As a result, we were able to operate the robot and read laser scan readings from within the simulation. 

* Designed a 3D Model (Base and Wheels) in SolidWorks and Exported.
For reference Go thorugh the [dolly.urdf.xacro](https://github.com/mdileepkumar438/ROS_Autonomous_Mobile_Robot/blob/main/urdf/dolly.urdf.xacro)

<img width="700" alt="Screenshot 2022-10-14 at 4 30 03 PM" src="https://user-images.githubusercontent.com/102908088/213444266-c45f4a5b-cb63-483e-b65a-f4d6b3348d28.png">

<img width="700" alt="Screenshot 2022-10-14 at 4 30 48 PM" src="https://user-images.githubusercontent.com/102908088/213444294-d6444b93-6577-41c5-82bc-6e901d84c2c9.png">

* Front-Arm is Designed with Inertial properties, as show in the below image

<img width="700" alt="Screenshot 2022-10-14 at 4 36 50 PM" src="https://user-images.githubusercontent.com/102908088/213445096-3e17f83d-4d77-4417-bd0b-b1a38cb11e6d.png">

* Adding Differential Drive Plugin to Drive.

<img width="700" alt="Screenshot 2022-10-14 at 4 39 56 PM" src="https://user-images.githubusercontent.com/102908088/213445943-cec78b3a-8ce2-47ea-9f43-ce87c647f6da.png">

* Wheel Transmission 



<img width="700" alt="Screenshot 2022-10-14 at 4 41 56 PM" src="https://user-images.githubusercontent.com/102908088/213446149-627ef478-f793-4e28-ad6d-7af93e5f2dae.png">

* Final Design of the Bot is Designed, which can hold the Object/Ball from TOP and able to move the small/medium Balls with front-Arms

<img width="400" alt="Screenshot 2022-10-14 at 4 46 11 PM" src="https://user-images.githubusercontent.com/102908088/213446789-589eb719-3425-43db-9aea-199c1a5a0efa.png">



- As soon as I had mastered the fundamentals of working with a custom mobile robot, I switched to the well-known ROS package SLAM, which has several nodes for mapping an environment. I used the Gmapping Node with a lidar sensor as a source.
Then a 3D model of an assessment world (Turlte world) was brought in, from which a map was made. 

<img width="300" alt="Screenshot 2022-10-14 at 4 58 06 PM" src="https://user-images.githubusercontent.com/102908088/213449066-164b2f52-f330-477a-bad5-5996f2802c76.png"> <img width="300" alt="Screenshot 2022-10-14 at 4 01 18 PM" src="https://user-images.githubusercontent.com/102908088/213449155-da82b477-a2fc-40b6-867e-6c605ab4b356.png">


As you can see here [Assessment_map](https://github.com/mdileepkumar438/ROS_Autonomous_Mobile_Robot/blob/main/config/Assesment_world.pgm)

- Autonomous Navigation using Gazebo Model. The robot needs to perform Autonomous driving using Navigation and Path Planning algorithms is still in Testing.
