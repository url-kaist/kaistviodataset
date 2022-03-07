# KAIST VIO dataset (RA-L'21 w/ ICRA Option)

## Remark
**This repository has been merged into [UrbanRoboticsLab_Git](https://github.com/url-kaist/KAIST_VIO_Dataest).
Please refer, fork, or post your issues on that repository from now on.
(however, I'll keep my eyes on both repositories.)**

<br><br>

##
Official page of [*"Run Your Visual-Inertial Odometry on NVIDIA Jetson: Benchmark Tests on a Micro Aerial Vehicle"*](https://ieeexplore.ieee.org/abstract/document/9416140), which is accepted by RA-L with ICRA'21 option


<div align="center">
  
  [![video](https://img.shields.io/badge/YouTube-B31B1B.svg)](https://www.youtube.com/watch?v=nZzgyhNimLI)  
  [![arxiv](https://img.shields.io/badge/arXiv-2103.01655-B31B1B.svg)](https://arxiv.org/abs/2103.01655)
  [![journal](https://img.shields.io/badge/paper-RA_L%202021-4b44ce.svg)](https://ieeexplore.ieee.org/abstract/document/9416140)

</div>


<!--
#### [[Video](https://www.youtube.com/watch?v=nZzgyhNimLI)] [[Preprint Paper](https://arxiv.org/abs/2103.01655)]
-->


***
This is the dataset for testing the robustness of various VO/VIO methods

You can download the whole dataset on [KAIST VIO dataset](https://urserver.kaist.ac.kr/publicdata/KAIST_VIO_Dataset/kaist_vio_dataset.zip)

***
<div>
<img src="https://user-images.githubusercontent.com/45934290/98090400-5054ec00-1ec7-11eb-9832-291dc9dbbabf.gif" width="320" height="240" />
<img src="https://user-images.githubusercontent.com/45934290/98204512-82bf2180-1f79-11eb-87c1-66ed70eaae3b.gif" width="320" height="240" /><br>

    
# Contents
    
1. [Trajectories](#Trajectories)
2. [Downloads](#Downloads)
3. [Dataset format](#Dataset-format)
4. [Setup](#Setup)
5. [Citation](#Citation)
<br><br>



## Trajectories
<img width="500" src="https://user-images.githubusercontent.com/45934290/96549200-222db480-12ea-11eb-8273-30d08be27316.png"><br>
+ Four different trajectories: *circle, infinity, square,* and *pure_rotation*.
+ Each trajectory has three types of sequence: *normal speed, fast speed, and rotation*.
+ The *pure rotation* sequence has only *normal speed, fast speed* types<br><br>

## Downloads
You can download a single ROS bag file from the link below. (or whole dataset from [KAIST VIO dataset](https://urserver.kaist.ac.kr/publicdata/KAIST_VIO_Dataset/kaist_vio_dataset.zip))<br>
| Trajectory | Type | ROS bag download |
| :---:        |     :---      | :---:   |
| **circle**   | normal<br>fast<br>rotation  | [link](https://urserver.kaist.ac.kr/publicdata/KAIST_VIO_Dataset/circle/circle.bag)<br>[link](https://urserver.kaist.ac.kr/publicdata/KAIST_VIO_Dataset/circle/circle_fast.bag)<br>[link](https://urserver.kaist.ac.kr/publicdata/KAIST_VIO_Dataset/circle/circle_head.bag) |
| **infinity**   | normal<br>fast<br>rotation  | [link](https://urserver.kaist.ac.kr/publicdata/KAIST_VIO_Dataset/infinite/infinite.bag)<br>[link](https://urserver.kaist.ac.kr/publicdata/KAIST_VIO_Dataset/infinite/infinite_fast.bag)<br>[link](https://urserver.kaist.ac.kr/publicdata/KAIST_VIO_Dataset/infinite/infinite_head.bag) |
| **square**   | normal<br>fast<br>rotation  | [link](https://urserver.kaist.ac.kr/publicdata/KAIST_VIO_Dataset/square/square.bag)<br>[link](https://urserver.kaist.ac.kr/publicdata/KAIST_VIO_Dataset/square/square_fast.bag)<br>[link](https://urserver.kaist.ac.kr/publicdata/KAIST_VIO_Dataset/square/square_head.bag) |
| **rotation**   | normal<br>fast  | [link](https://urserver.kaist.ac.kr/publicdata/KAIST_VIO_Dataset/rotation/rotation.bag)<br>[link](https://urserver.kaist.ac.kr/publicdata/KAIST_VIO_Dataset/rotation/rotation_fast.bag) |

<br><br>
## Dataset format
<img width="300" src=https://user-images.githubusercontent.com/45934290/96554882-13e39680-12f2-11eb-9464-135aca484dc4.png><br>

+ Each set of data is recorded as a **ROS bag** file.
+ Each **data** sequence contains the followings:
    + stereo infra images (w/ emitter turned off)
    + mono RGB image
    + IMU data (3-axes accelerometer, 3-axes gyroscopes)
    + 6-DOF Ground-Truth
+ ROS topic
    + Camera(30 Hz): *"/camera/infra1(2)/image_rect_raw/compressed", "/camera/color/image_raw/compressed"*
    + IMU(100 Hz): *"/mavros/imu/data"* 
    + Ground-Truth(50 Hz): *"/pose_transformed"* 
+ In the **config** directory
    + trans-mat.yaml: translational matrix between the origin of the Ground-Truth and the VI sensor unit. 
    <br>(the offset has already been applied to the bag data, and this YAML file has estimated offset values, just for reference. To benchmark your VO/VIO method more accurately, you can use your alignment method with other tools, like origin alignment or Umeyama alignment from [evo](https://github.com/MichaelGrupp/evo))
    + imu-params.yaml: estimated noise parameters of Pixhawk 4 mini
    + cam-imu.yaml: Camera intrinsics, Camera-IMU extrinsics in kalibr format


<br><br>
## Setup
#### - Hardware
<div>
<img width="300" src=https://user-images.githubusercontent.com/45934290/96550149-77b69100-12eb-11eb-91da-2d413cae40d6.png>
<img width="313" src=https://user-images.githubusercontent.com/45934290/96550443-d419b080-12eb-11eb-805d-dab8393dd6f0.png>
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Fig.1 Lab Environment  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Fig.2 UAV platform<br>

+ **VI sensor unit**
    + camera: Intel Realsense D435i (640x480 for infra 1,2 & RGB images)
    + IMU: Pixhawk 4 mini
    + VI sensor unit was calibrated by using [kalibr](https://github.com/ethz-asl/kalibr)
    <br>
+ **Ground-Truth**
    + OptiTrack Prime<sup>X</sup> 13 motion capture system with six cameras was used
    + including 6-DOF motion information.
    <br><br>
    

#### - Software (VO/VIO Algorithms): How to set each (publicly available) algorithm on the jetson board
| VO/VIO | Setup link |
| :---:        |     :---:  |     
| **VINS-Mono**   | [link](https://github.com/zinuok/VINS-MONO) |
| **ROVIO**   | [link](https://github.com/zinuok/Rovio) |
| **VINS-Fusion**   | [link](https://github.com/zinuok/VINS-Fusion) |
| **Stereo-MSCKF**   | [link](https://github.com/zinuok/MSCKF_VIO) |
| **Kimera**   | [link](https://github.com/zinuok/Kimera-VIO-ROS) |


## Citation

If you use the dataset in an academic context, please cite the following publication:

    @article{jeon2021run,
    title={Run Your Visual-Inertial Odometry on NVIDIA Jetson: Benchmark Tests on a Micro Aerial Vehicle},
    author={Jeon, Jinwoo and Jung, Sungwook and Lee, Eungchang and Choi, Duckyu and Myung, Hyun},
    journal={arXiv preprint arXiv:2103.01655},
    year={2021}
    }

## Lisence

This datasets are released under the Creative Commons license (CC BY-NC-SA 3.0), which is free for non-commercial use (including research).
