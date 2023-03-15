# rdws_cloud_platform_r
## 1.summary
* **Author**：CrawlerWheel
* **Abstract**：机器人巡检云平台-机器人端。将yolov5警情目标检测权重模型转换后，进行tensorrtx加速，并整合进行ROS系统当中；根据数据形式的需求自定义检测结果的ROS消息结构；解决ROS系统跨平台数据传输问题。目前系统已在Jetson相机和Zed2i相机上进行了适配。
* **yolov5_pub_mono_node.launch**：该launch文件是适配了Jetson单目相机的ROS警情检测节点，通常来说对CSI相机均适用。
* **yolov5_pub_node.launch**：该launch文件是适配了Zed2i相机的ROS警情检测节点，但通常来说对USB网络相机均适用。

## 2.Prerequisites
### C++11 or C++0x Compiler
### ROS
Tested with Melodic in Ubuntu18.04.
### OpenCV
Tested with OpenCV 3.2.0.
### cuda
Tested with Cuda 10.2.
### Gstreamer Install
```
sudo add-apt-repository universe
sudo add-apt-repository multiverse
sudo apt-get update
sudo apt-get install gstreamer1.0-tools gstreamer1.0-alsa gstreamer1.0-plugins-base gstreamer1.0-plugins-good gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly gstreamer1.0-libav
sudo apt-get install libgstreamer1.0-dev libgstreamer-plugins-base1.0-dev libgstreamer-plugins-good1.0-dev libgstreamer-plugins-bad1.0-dev
```
### RosBridge Install
`sudo apt-get install ros-<rosdistro>-rosbridge-server` 
### frp Install
`git clone https://github.com/fatedier/frp.git`

## 3.Build
```
mkdir -p catkin_workspace/src
cd ./catkin_workspace/src
git clone https://github.com/CrawlerWheel/rdws_cloud_platform_r.git
cd ..
catkin_make
```

## 4.Environment Configuration
找到你的.bashrc环境配置脚本文件，并添加以下配置信息
```
export ROS_PACKAGE_PATH=${ROS_PACKAGE_PATH}:/home/catkin_workspace/src #替换为你的 URL
export PATH=${PATH}:/usr/local/cuda-10.2/bin # cuda compiler 路径配置
source /home/wheeltec/catkin_ws/devel/setup.bash 

```
`. .bashrc` 在当前终端生效

## 5.By The Wey
如果你想通过主程序的运行直接看到警情检测的效果，可以将`yolov5_rospub_mono.cpp` 和`yolov5_rospub.cpp`两main函数中的如下代码取消注释：
```
ssss
```














