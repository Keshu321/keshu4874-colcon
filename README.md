# Using colcon to build packages 

## Background

Iterations of the ROS build tools like catkin make, catkin make isolated, catkin tools, and ament tools include colcon.  

## Prerequisites 

## Install colcon

```
sudo apt install python3-colcon-common-extensions
```
![image](https://user-images.githubusercontent.com/92859942/194816252-1e986b97-08cb-43bf-a8d9-e3c5c32080a8.png)


## Install ROS

 in order to build the example we must set ROS 2.

## Create a workspace 

To build  our workspace, we need to create the directory ros2 ws:

```
mkdir -p ~/ros2_ws/src
cd ~/ros2_ws
```
![image](https://user-images.githubusercontent.com/92859942/194816321-06ff339f-7c9b-4506-b21b-393db63612a1.png)


The workspace currently only has the empty directory src. 

## Add some sources

![image](https://user-images.githubusercontent.com/92859942/194818010-3435dcd9-77e7-4dab-8397-4896b5978a68.png):

```
git clone https://github.com/ros2/examples src/examples -b foxy
```
![image](https://user-images.githubusercontent.com/92859942/194816461-82c17358-5274-48d0-8b05-d61509fdde86.png)

The source code for the ROS 2 examples should now be in the workspace:

```
└── src
    └── examples
        ├── CONTRIBUTING.md
        ├── LICENSE
        ├── rclcpp
        ├── rclpy
        └── README.md

4 directories, 3 files
```

## Build the workspace

```
colcon build --symlink-install
```
![image](https://user-images.githubusercontent.com/92859942/194816739-d2ecf741-9fd8-42c3-94ac-097e6f9c07cf.png)


We should see the build, install, and log directories once the build is complete:
```
.
├── build
├── install
├── log
└── src

4 directories, 0 files
```
## Run tests
Test the newly created packages by executing the following:

```
colcon test
```
![image](https://user-images.githubusercontent.com/92859942/194817137-4a08ae4a-18a4-441a-8397-d2b3a692a27d.png)

## Source the environment

```
. install/setup.bash
```

# Try a demo

Colcon's executables can be run using the provided environment. Let's examine one of the subscriber nodes in the examples:

```
ros2 run examples_rclcpp_minimal_subscriber subscriber_member_function
```
![image](https://user-images.githubusercontent.com/92859942/194817394-f67439fd-6fe3-46d1-98bb-200cac8dd941.png)


now we are ready tolaunch a publisher node in another terminal 

```
ros2 run examples_rclcpp_minimal_publisher publisher_member_function
```
![image](https://user-images.githubusercontent.com/92859942/194817458-0e69eae8-a75c-4e4a-b9be-0c855c530f8e.png)

we can see a messages from the publisher and subscriber with numbers incrementing.

# Create your own package
```
echo "source /usr/share/colcon_cd/function/colcon_cd.sh" >> ~/.bashrc
echo "export _colcon_cd_root=/opt/ros/foxy/" >> ~/.bashrc
```

## Setup colcon tab completion

```
echo "source /usr/share/colcon_argcomplete/hook/colcon-argcomplete.bash" >> ~/.bashrc
```
![image](https://user-images.githubusercontent.com/92859942/194817643-8d97107c-fbcc-46f9-b585-0d5843560be2.png)
