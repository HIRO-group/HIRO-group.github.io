---
type: article
title: "MARBLE SubT Finals Dataset"
---

We present the **MARBLE SubT Finals**
dataset. It consists of xx sequences, recorded in the DARPA SubT Finals competition course, setup in the Kentucky Megacavern. The data includes xx minutes of 3D lidar, IMU, and camera
data. The full dataset, including sensor data, calibration sequences,
and evaluation scripts can be downloaded here.

### Downloads

We have organized our dataset using the Automous Systems Lab (ASL) dataset
format, though our dataset additionally provides files for the photometric
camera calibration and light calibration. Each sequence is available at
full-resolution and separated into its own zip file. **Vicon data for ASPEN Lab coming soon**

| Sequence Name                       | Length (seconds) | kitti link                                                                  | rosbag link         | comment                              |
| ----------------------------------- | ---------------: | :-------------------------------------------------------------------------: | :-----------:       | ------------------------------------ |

### Platforms

![Photo of Spot Platform](/img/marble/spot.jpg){:width="100%"}
![Photo of Husky Platform](/img/marble/husky.jpg){:width="100%"}

The Spot Platform contains the following components:

* Lidar Sensor: Ouster OS1; 10Hz; 64 beams; 1-degree angular accuracy; angular resolution 0.35-degree horizontal, 0.7-degree vertical; 3cm range accuracy; field of view 360-degree horizontal, 45-degree vertical; max range 120m; 65,536 points per scan
* IMU: Lord Microstrain 3DM-GX5-25; 300Hz
* Cameras:

The Husky Platform contains the following componenets:

* Lidar Sensor: Ouster OS1; 10Hz; 64 beams; 1-degree angular accuracy; angular resolution 0.35-degree horizontal, 0.7-degree vertical; 3cm range accuracy; field of view 360-degree horizontal, 45-degree vertical; max range 120m; 65,536 points per scan
* IMU: Lord Microstrain 3DM-GX5-25; 300Hz
* Cameras: 

### Evaluation

### Calibration

### License

This dataset is released under the [Apache 2.0 license](https://www.apache.org/licenses/LICENSE-2.0). 

### CITATION

A paper using this dataset has been submitted to XXXX. While this is awaiting publication, please cite:

*xxxx
