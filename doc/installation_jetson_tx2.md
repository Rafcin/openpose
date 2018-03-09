OpenPose - Installation on Nvidia Jetson TX2
====================================
Note that OpenPose for Nvidia Jetson TX2 was developed and it is maintained by the community. The OpenPose authors will not be able to provide official support for it.


## Contents
1. [Requirements](#requirements)
2. [Installation](#installation)
3. [Usage](#usage)


## Requirements
Jetson TX2 just flashed with [JetPack 3.1](https://developer.nvidia.com/embedded/jetpack)

Notes:

- Installation is similar to Jetson TX1 and you can follow this [video tutorial](https://www.youtube.com/watch?v=RJkOGMC8IrY).
- If you are installing from a virtual machine host, installation may need to be done in two steps, please refer to [this solution](https://devtalk.nvidia.com/default/topic/1002081/jetson-tx2/jetpack-3-0-install-with-a-vm/).
- Be sure to complete both OS flashing and CUDA / cuDNN installation parts before installation.


## Installation
Use the following script for installation of both caffe and OpenPose: 
```
./ubuntu/install_caffe_and_openpose_JetsonTX2_JetPack3.1.sh
```
Notes:
- Some people may be missing dependencies for OpenCV, if that is the case use [Jetsonhacks Opencv JetsonTx2 Install Script](https://github.com/jetsonhacks/buildOpenCVTX2) to install Opencv 3. Do keep in mind that you will need to manually make OpenCV.
- If you choose to install OpenCV 3, modify makefiles Makefile.config.Ubuntu16_cuda8.example and Makefile.config.Ubuntu16_cuda8_JetsonTX2 to enable OpenCV 3.


## Usage
It is for now recommended to use an external camera with the demo. To get to decent FPS you need to lower the net resolution:
```
./build/openpose/openpose.bin -camera_resolution 640x480 -net_resolution 128x96
```

To activate hand or face resolution please complete this command with the following options (warning, both simultaneously will cause out of memory error):
```
--hand -hand_net_resolution 256x256
--face -face_net_resolution 256x256
``` 
