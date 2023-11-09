
# Introduction
`OpenPCDet`  is a clear, simple, self-contained open source project for LiDAR-based 3D object detection.  

It is also the official code release of  [`[PointRCNN]`](https://arxiv.org/abs/1812.04244),  [`[Part-A2-Net]`](https://arxiv.org/abs/1907.03670),  [`[PV-RCNN]`](https://arxiv.org/abs/1912.13192),  [`[Voxel R-CNN]`](https://arxiv.org/abs/2012.15712),  [`[PV-RCNN++]`](https://arxiv.org/abs/2102.00463)    [`[MPPNet]`](https://arxiv.org/abs/2205.05979)  and  [`[PointPillars]`](https://arxiv.org/abs/1812.05784). 

This project is based on the ROS (Robot Operating System) and utilizes the PointPillars algorithm for 3D point cloud object detection. It aims to achieve recognition and tracking of objects in the surrounding environment, providing environmental perception and decision support for autonomous driving.  

![PointPillar](https://github.com/xiaoruoxu/pointpillars_ros/blob/main/docs/PointPillar.jpg)

# Installation
## Requirements
All the codes are tested in the following environment:
-   Ubuntu 20.04
-   Python 3.8
-   CUDA 10.2
-   PyTorch 1.9.0
-   ROS Noetic  
## 1 Preparations
**1.1 Install Pytorch**
```
conda create -n pointpillars_ros python=3.8  
conda activate pointpillars_ros  
conda install pytorch==1.9.0 torchvision==0.10.0 torchaudio==0.9.0 cudatoolkit=10.2 -c pytorch  
```
**1.2 Other dependencies**
```
sudo apt-get install ros-noetic-pcl-ros  
sudo apt-get install ros-noetic-jsk-recognition-msgs  
sudo apt-get install ros-noetic-jsk-rviz-plugins  
```
**1.3 Creating workspace**
```
mkdir -p ~/pointpillars_ws/src && cd pointpillars_ws/ 
catkin_make  
```
**1.4 Install OpenPCDet**
```
cd pointpillars_ws     
```
Please refer [INSTALL.md](https://github.com/open-mmlab/OpenPCDet/blob/master/docs/INSTALL.md), [DEMO.md](https://github.com/open-mmlab/OpenPCDet/blob/master/docs/DEMO.md) and [GETTING_STARTED.md](https://github.com/open-mmlab/OpenPCDet/blob/master/docs/GETTING_STARTED.md) for the installation of `OpenPCDet`.

**1.5 Install ROS bag**
```
cd pointpillars_ws  
mkdir bag  
```
Please refer [kitti2bag](https://github.com/tomas789/kitti2bag) to download ROS bag and put it into bag/  
## 2 Download Pointpillars_ros
**2.1 Clone this repository**
```
cd pointpillars_ws/src  
git clone https://github.com/xiaoruoxu/pointpillars_ros.git  
```
**2.2 Move files from OpenPCDet to respective locations**

Copy and paste **all the files from OpenPCDet/tools directory** and **OpenPCDet/pcdet directory** into the **src/pointpillars/tools** folder.

**2.3 Code modification**

 - Please replace 'xxx' with your own username in the **ros.py** and the **pointpillars.launch**.
 - Change the path in the **kitti_dataset.yaml** of the **pointpillar.yaml** to an absolute path.
 # Demo
 Here we provide a quick demo to test a pretrained model on the ROS bag and visualize the predicted results.
 ```
cd pointpillars_ws && conda activate pointpillars_ros  
source devel/setup.bash  
roslaunch pointpillars_ros pointpillars.launch  
```
Then you could see the predicted results with visualized point cloud as follows:

![pointpillars_ros](https://github.com/xiaoruoxu/pointpillars_ros/blob/main/docs/pointpillars_ros.jpg)
