# kaistviodataset

***
This is the dataset for testing the robustness of various VO/VIO

You can download the dataset on [here]("https://www.google.com/")
***
# Index
### 1. Setup
####    &nbsp;&nbsp;&nbsp;&nbsp;● Eigen
####    &nbsp;&nbsp;&nbsp;&nbsp;● Ceres solver
### 2. Ground-Truth trajectories
### 3. Jetson Boards
####    &nbsp;&nbsp;&nbsp;&nbsp;● Actu#### ● Uploaded folders for following setup: D435i, pixhawk4 mini 
#### ● for using your own sensor setup, you have to get a calibration data using [kalibr](https://github.com/zinuok/kalibr)ally, there is no installation difference among TX2, Xavier, and NX
### 4. Run
<br><br>


### Setup
<div>
<img width="300" src=https://user-images.githubusercontent.com/45934290/96550149-77b69100-12eb-11eb-91da-2d413cae40d6.png>
<img width="313" src=https://user-images.githubusercontent.com/45934290/96550443-d419b080-12eb-11eb-805d-dab8393dd6f0.png>
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Fig.1 Lab Environment  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Fig.2 UAV platform

+ **hardware setup**
    + jetson TX2 - Jetpack 4.2
    + jetson AGX Xavier
    + jetson Xavier NX - Jetpack 4.4
    + realsense D435i (color, infra1, infra2)
    + pixhawk4 mini
    <br>
+ **software setup**
    + Ubuntu: 18.04 
    + ROS: Melodic
    + OpenCV 3.4.1
    <br>
+ **CPU ver. github link**: [HKUST-Aerial-Robotics](https://github.com/HKUST-Aerial-Robotics/VINS-Fusion)
+ **GPU ver. github link**: [HKUST-Aerial-Robotics](https://github.com/pjrambo/VINS-Fusion-gpu)

### Ground-Truth trajectories
<img width="600" src="https://user-images.githubusercontent.com/45934290/96549200-222db480-12ea-11eb-8273-30d08be27316.png">



