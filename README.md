# KAIST VIO dataset

***
This is the dataset for testing the robustness of various VO/VIO methods

You can download the whole dataset on [KAIST VIO dataset](https://www.google.com/)
***
# Index
### 1. Trajectories
### 2. Downloads
### 3. Available data
### 4. Setup
<br><br>



### 1. Trajectories
<img width="600" src="https://user-images.githubusercontent.com/45934290/96549200-222db480-12ea-11eb-8273-30d08be27316.png"><br>
+ Four different trajectories: *circle, infinity, square,* and *pure_rotation*.
+ Each trajectory has three types of sequence: *normal speed, fast speed, and rotation*.
+ The *pure rotation* sequence has only *normal speed, fast speed* types<br><br>

### 2. Downloads
+ You can download a single file from the link below. 
| Trajectory | Type | ROS bag download |
| :---:        |     :---      | :---:   |
| **circle**   | normal<br>fast<br>rotation  | [here](https://www.google.com/)<br>[here](https://www.google.com/)<br>[here](https://www.google.com/) |
| **infinity**   | normal<br>fast<br>rotation  | [here](https://www.google.com/)<br>[here](https://www.google.com/)<br>[here](https://www.google.com/) |
| **square**   | normal<br>fast<br>rotation  | [here](https://www.google.com/)<br>[here](https://www.google.com/)<br>[here](https://www.google.com/) |
| **rotation**   | normal<br>fast  | [here](https://www.google.com/)<br>[here](https://www.google.com/) |

<br><br>
### 3. Available data
<img width="300" src=https://user-images.githubusercontent.com/45934290/96554882-13e39680-12f2-11eb-9464-135aca484dc4.png><br>

+ Each set of data is recorded as a **ROS bag** file.
+ Each **data** sequence contains followings:
    + a pair of stereo infra images (w/ emitter turned off)
    + one RGB image
    + IMU data (3-axes accelerometer, 3-axes gyroscopes)
    + 6-DOF Ground-Truth
+ ROS topic
    + Camera: "/camera/infra1/image_rect_raw", "/camera/infra2/image_rect_raw", "/camera/color/image_raw" (30 Hz)
    + IMU: "/mavros/imu/data" (100 Hz)
    + Ground-Truth: "/pose_transformed" (50 Hz)
+ In **config** directory
    + trans-mat.yaml: translational matrix between the origin of the Ground-Truth and the VI sensor unit. (just for reference)
    + imu-params.yaml: estimated noise parameters of Pixhawk 4 mini
    + cam-imu.yaml: Camera intrinsics, Camera-IMU extrinsics in kalibr format


<br><br>
### 4. Setup
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



