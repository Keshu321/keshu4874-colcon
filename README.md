# Using colcon to build packages
## requirements 
install colon and ros 2 

```
sudo apt install python3-colcon-common-extensions
```
![image](https://user-images.githubusercontent.com/92859942/194760355-09031bc2-20dc-4dca-bd14-a5dd052d7fa7.png)

#Create a workspace

```
mkdir -p ~/ros2_ws/src
cd ~/ros2_ws
```
At this point the workspace contains a single empty directory src:

```
.
└── src

1 directory, 0 files
```
![image](https://user-images.githubusercontent.com/92859942/194760535-d33c9cf0-1296-4a45-be9b-6f06fdcb29f8.png)


## Add some sources
Let’s clone the examples repository into the src directory of the workspace:

```
sudo apt install git
git clone https://github.com/ros2/examples src/examples -b foxy
```
Now the workspace should have the source code to the ROS 2 examples:

```
.
└── src
    └── examples
        ├── CONTRIBUTING.md
        ├── LICENSE
        ├── rclcpp
        ├── rclpy
        └── README.md

4 directories, 3 files
```
![image](https://user-images.githubusercontent.com/92859942/194760717-eb6581e9-2337-424f-9444-cc41d6e0eadb.png)

# Build the workspace

```
colcon build --symlink-install
```
After the build is finished, we should see the build, install, and log directories:

```
.
├── build
├── install
├── log
└── src

4 directories, 0 files
```
![image](https://user-images.githubusercontent.com/92859942/194760782-fefb759d-e3f6-4b52-9532-6d39315a7eec.png)

# run test

```
colcon test
```
## source the environment 
```
install/setup.bash
```
# try a demo

we can run executables built by colcon after environment sourced.
Let’s run a subscriber node :

```
ros2 run examples_rclcpp_minimal_subscriber subscriber_member_function
```
In another terminal, let’s run a publisher node 

```
ros2 run examples_rclcpp_minimal_publisher publisher_member_function
```

we can see a message 
![image](https://user-images.githubusercontent.com/92859942/194761063-c5564f00-c435-4b9c-ab30-aef0183a072b.png)


# Create your own package

```
echo "source /usr/share/colcon_cd/function/colcon_cd.sh" >> ~/.bashrc
echo "export _colcon_cd_root=/opt/ros/foxy/" >> ~/.bashrc
```
# Setup colcon tab completion

```
echo "source /usr/share/colcon_argcomplete/hook/colcon-argcomplete.bash" >> ~/.bashrc
```
