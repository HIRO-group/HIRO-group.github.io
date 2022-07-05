---
type: article
title: "MARBLE SubT Finals Dataset"
---

We present the **MARBLE SubT Finals**
dataset. It consists of sensor data, recorded in the DARPA SubT Finals competition course, setup in the Kentucky Megacavern. The data specificallyincldues 3D lidar from an Ouster OS1-64 beam lidar, IMU, and RGB camera
data. The full dataset, including sensor data, calibration sequences,
and evaluation scripts can be downloaded here.

### Downloads

| File | Agent | Size [GB] | Length (hh:mm:ss) |
| -------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-------: | :---------------: |
| Base Station Screen Capture 10X ([Video](https://drive.google.com/file/d/1NiiZ1O-ar1ht9fx0A7uu1sU-vYs_OEMw/view?usp=sharing)) &nbsp;   &nbsp;   &nbsp;   &nbsp;   &nbsp;  | BS | 0.1 | 00:06:08       |
| Base Station Data ([Rosbag](https://drive.google.com/file/d/1pu8jfVmEhdba-_H0PwJ2AIA9_fIIIaIa/view?usp=sharing)) &nbsp;  | BS | 20.9 | 01:08:48       |
| D02 FPV Footage 5X ([Front Video](https://drive.google.com/file/d/1MqaEi-Yc-QF_GMpJXYCgCl1hfgjQGouy/view?usp=sharing), [Left Video](https://drive.google.com/file/d/1K3e1SfBP36E-kD6zdKndQrllCt-VCiqJ/view?usp=sharing), [Right Video](https://drive.google.com/file/d/1kMoixfGoJQwT3qtiLopX5Sje-scnRvM-/view?usp=sharing)) &nbsp;  | D02 | 0.1 | 00:14:04       |
| D02 Output Data ([Rosbag](https://drive.google.com/file/d/1ATUuMbJqWjFpqFYOATFXki4veJLLMKFO/view?usp=sharing)) &nbsp;  | D02 | 12.3 | 01:18:03       |
| D02 FPV Data ([Rosbag](https://drive.google.com/file/d/162WhyaaJI8u9Lqywdt89mD2ZTvWpNvgk/view?usp=sharing)) &nbsp;  | D02 | 11.6 | 01:18:40       |
| D01 FPV Footage 5X ([Front Video](https://drive.google.com/file/d/17KFC-pw6IRe3mMUjmmimJTKuEOGRvUgc/view?usp=sharing), [Left Video](https://drive.google.com/file/d/1wrvTfG2ZmcdQIb2_ZMCraGS5ejmZwMkc/view?usp=sharing), [Right Video](https://drive.google.com/file/d/1SlLTr3EjW7_Aes6vfdiS-vQIh_rsHnBW/view?usp=sharing)) &nbsp;  | D01 | 0.1 | 00:14:04       |
| D01 Output Data ([Rosbag](https://drive.google.com/file/d/18YgU-kMDqf5MeM8QgN12zlYW1XeJi6fG/view?usp=sharing)) &nbsp;  | D01 | 8.3  | 01:07:28       |
| D01 FPV Data ([Rosbag](https://drive.google.com/file/d/1Ij9RHCtcKrcqMaxVqZS4YmuGruG2z09g/view?usp=sharing)) &nbsp;  | D01 | 6.7  | 00:45:35       |
| H02 FPV Footage 5X ([Front Video](https://drive.google.com/file/d/1FAj9UFXr49enaaGbLxh321g9dY9-6of3/view?usp=sharing)) &nbsp;  | H02 | 0.1 | 00:07:07       |
| H02 Output Data ([Rosbag](https://drive.google.com/file/d/1W7MbGklgde_LyixR6IMpZZveaBB8pNyH/view?usp=sharing)) &nbsp; &nbsp;  | H02 | 6.5  | 00:40:00       |
| H02 FPV Data ([Rosbag](https://drive.google.com/file/d/1Ud0hSqkWcT2mml9i7MALVVWVwjttO2D-/view?usp=sharing)) &nbsp; &nbsp;  | H02 | 2.0  | 00:39:44       |
| H01 FPV Footage 5X ([Front Video](https://drive.google.com/file/d/1LHd1SVs6zKf0loUlCXBBroToeERnJK9U/view?usp=sharing)) &nbsp;  | H01 | 0.1 | 00:13:51       |
| H01 Output Data ([Rosbag](https://drive.google.com/file/d/1guamP0_i_a0pdYtKafg4PKlV6li2IxM2/view?usp=sharing)) &nbsp; &nbsp; &nbsp; &nbsp;  | H01 | 10.2 | 01:17:45 |
| H01 FPV Data ([Rosbag](https://drive.google.com/file/d/1eFMp24-2cpqdcNmwmY13Ee-4Y092NQDM/view?usp=sharing)) &nbsp;  | H01 | 3.8  | 01:17:27 |


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


### License

This dataset is released under the [Apache 2.0 license](https://www.apache.org/licenses/LICENSE-2.0). 

### CITATION

Team MARBLE has submitted a special issues paper to the Field Robotics Journal titled "Flexible Supervised Autonomy for Exploration in
Subterranean Environments," which is current in review.
