Python ROS2 pointcloud retriever for IWR6843AOPEVM mmWave device


![myimage](https://github.com/syed-dce/IWR6843AOPEVM-pointcloud/blob/main/assets/a.jpg)


Prerequisites:-  
ROS2 (Ubuntu 18.04/ Ubuntu 20.04)  
Python3 (3.8)  
IWR6843AOPEVM  mmWave radar   

Installation:-  
Clone the repo to workspace  
cd ~/ros2_ws/src/  
git clone https://github.com/nhma20/iwr6843aop_pub.git  
Colcon build package  
cd ~/ros2_ws/  
colcon build --packages-select iwr6843aop_pub  


Usage:-  
Plug in IWR6843AOPEVM, check PORT/ devide nodes (default /dev/ttyUSB0)  

Run ros package (make sure /opt/ros/dashing/setup.bash and <ros2_workspace>/install/setup.bash are sourced)  

ros2 run iwr6843aop_pub pcl_pub  
example with ROS2 parameters:  

ros2 run iwr6843aop_pub pcl_pub --ros-args -p cli_port:=/dev/ttyUSB0 -p data_port:=/dev/ttyUSB1 -p cfg_path:=/home/nm/ros2_ws/src/iwr6843aop_pub/cfg_files/90deg_noGroup_18m_30Hz.cfg  
Launch example with default parameters:  

ros2 launch iwr6843aop_pub default_parameters.launch.py  
When loading a cfg with a different antenna configuration than the previous, IWR6843AOP device must be power cycled - can be done easily by pressing the RST_SW switch, or simply unplugging and replugging the USB cable.  

Visualize with rviz  

rviz2  
'Add' a new display (lower left corner)  

Select 'By topic' ribbon  

Find 'iwr6843_pcl PointCloud2' and add it  

Edit 'Fixed Frame' to 'iwr6843_frame'. (use a 'static_transform_publisher' to transform to another frame)  

(Optional) Set point size at PointCloud2 -> Size (m) to 0.1 for better clarity  
