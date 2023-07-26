---
type: article
title: "ColoRadar Dataset"
---

We present the **Colorado mm-Wave Radar (ColoRadar)**
dataset. It consists of 52 sequences, recorded in mines, built environments, and in an urban creek path,
totaling more than 145 minutes of 3D FMCW radar, 3D lidar, and IMU
data. The full dataset, including sensor data, calibration sequences,
and evaluation scripts can be downloaded here.

For an explanation video of this dataset, please click the linked image below:

[![ColoRadar dataset](http://img.youtube.com/vi/kF2urbqBJPw/0.jpg)](https://youtu.be/kF2urbqBJPw "ColoRadar dataset")

### Downloads

We have organized our dataset using the Automous Systems Lab (ASL) dataset
format, though our dataset additionally provides files for the photometric
camera calibration and light calibration. Each sequence is available at
full-resolution and separated into its own zip file. **Vicon data for ASPEN Lab coming soon**

[Full COLORADAR data set](https://o365coloradoedu-my.sharepoint.com/:f:/g/personal/chhe5305_colorado_edu/Em9OXSOuarJCnm2Oyfr_6XgBtgLbtFuUOmjKKHSD-h5q_w?e=zHt1st&xsdata=MDV8MDF8fDYyYzgxM2JhNGI3YzQ4MjBkNmRhMDhkYjhjODI0MmEwfDNkZWQ4YjFiMDcwZDQ2Mjk4MmU0YzBiMDE5ZjQ2MDU3fDB8MHw2MzgyNTgyNjMyOTQ1MzEyOTB8VW5rbm93bnxWR1ZoYlhOVFpXTjFjbWwwZVZObGNuWnBZMlY4ZXlKV0lqb2lNQzR3TGpBd01EQWlMQ0pRSWpvaVYybHVNeklpTENKQlRpSTZJazkwYUdWeUlpd2lWMVFpT2pFeGZRPT18MXxMM1JsWVcxekx6RTVPamMwTkRSbVltRmhOVEk0WWpReE1qVTVOV0ppWXpkaE1Ea3hOVEUwTVRrNFFIUm9jbVZoWkM1emEzbHdaUzlqYUdGdWJtVnNjeTh4T1RvMlltSmpPR00zTUdJek9EZzBaalJqT0RNek56a3hNREF3TVRNMk1qSTFZVUIwYUhKbFlXUXVjMnQ1Y0dVdmJXVnpjMkZuWlhNdk1UWTVNREl5T1RVeU9EQTRNUT09fDkzMjMyMzM1ZWVlZjRkZWVkNmRhMDhkYjhjODI0MmEwfGE4YjU0MzY3ZWVhOTRkOGVhYTc3NzFlZDc2ZjQ0OTRj&sdata=d09yTERvYlVDNVNURTZ4MmJFNExwdXVFNFFMZGdHVTlJRlU5VlRtZm93MD0%3D)

### Sensor Rig

![Photo of sensor rig](/img/radar-sensor-thumbnail.png)

The sensor rig contains the following components:

* Cascaded Imaging Radar Sensor: Texas Instruments MMWCAS-RF-EVM
* Single Chip Radar Sensor: Texas Instruments AWR1843BOOST-EVM paired with a DCA1000-EVM for raw data capture
* Lidar Sensor: Ouster OS1; 10Hz; 64 beams; 1-degree angular accuracy; angular resolution 0.35-degree horizontal, 0.7-degree vertical; 3cm range accuracy; field of view 360-degree horizontal, 45-degree vertical; max range 120m; 65,536 points per scan
* IMU: Lord Microstrain 3DM-GX5-25; 300Hz

### Evaluation

To be included.
<!--
This benchmark provides two methods for ground-truthing. The three sequences
where the ground-vehicle is used, 3D positions at 10Hz were captured via a
Leica TCRP1203 R300. In all remaining sequences, we start and end in the same
position, permitting the use of total accumulated drift as another evaluation
metric. We provide the following scripts for evaluation, adapted from the [TUM
benchmark tools](https://vision.in.tum.de/data/datasets/rgbd-dataset/tools).
-->

### Calibration

We additionally include a decluttering calibration dataset, so that radar calibration
models may be inferred.

### License

This dataset is released under the [Apache 2.0 license](https://www.apache.org/licenses/LICENSE-2.0). 

### CITATION

This paper has been accepted to the International Journal of Robotics Research (IJRR) as of October 2021. While it's awaiting publication, please cite:
* Kramer A, Harlow K, Williams C, Heckman C. ColoRadar: The Direct 3D Millimeter Wave Radar Dataset. arXiv preprint arXiv:2103.04510. 2021 Mar 8.

