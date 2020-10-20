# kaistviodataset

***
This is the dataset for testing the robustness of various VO/VIO methods

You can download the whole dataset on [here](https://www.google.com/)
***
# Index
### 1. Setup
### 2. Trajectories
### 3. Available data
### 4. Downloads
<br><br>


### 1. Setup
<div>
<img width="300" src=https://user-images.githubusercontent.com/45934290/96550149-77b69100-12eb-11eb-91da-2d413cae40d6.png>
<img width="313" src=https://user-images.githubusercontent.com/45934290/96550443-d419b080-12eb-11eb-805d-dab8393dd6f0.png>
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Fig.1 Lab Environment  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Fig.2 UAV platform

<br><br>
+ **VI sensor unit**
    + camera: Intel Realsense D435i (30 Hz, 640x480 for infra 1,2 & RGB images)
    + IMU: Pixhawk 4 mini (100 Hz)
    + VI sensor unit was calibrated by using [kalibr](https://github.com/ethz-asl/kalibr) (50 Hz)
    <br>
+ **Ground-Truth**
    + OptiTrack Prime<sup>X</sup> 13 motion capture system with six cameras was used
    + including 6-DOF motion information.
    <br><br>

### 2. Trajectories
<img width="600" src="https://user-images.githubusercontent.com/45934290/96549200-222db480-12ea-11eb-8273-30d08be27316.png"><br>
KAIST VIO dataset includes four different trajectories: *circle, infinity, square,* and
*pure_rotation*.<br>
Each trajectory has three types of sequence: *normal speed, fast speed, and rotation*.<br>
(the *pure rotation* sequence has only *normal speed, fast speed* types)<br><br>

### 3. Available data
<img width="400" src=https://user-images.githubusercontent.com/45934290/96554882-13e39680-12f2-11eb-9464-135aca484dc4.png><br>

+ Each set of data is recorded as a **ROS bag** file.
+ Each sequence contains followings:
    + a pair of stereo infra images (w/ emitter turned off)
    + one RGB image
    + IMU data (3-axes accelerometer, 3-axes gyroscopes)
    + 6-DOF Ground-Truth




