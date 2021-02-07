# Livox_detection modified by ArtinX Team, SUSTech
This project based on [livox_detection](https://github.com/Livox-SDK/livox_detection) and has been modified to detect and track multiple objects by ArtinX Team, SUSTech.

## Main changes
### Done:
- `Upgrade to tensorflow 2`
- `Using C++ to reconstruct part of this project`
### Doing:
- `Continuous tracking`
- `Make methods and models more suitable to detect and track robots`
### To-Do:
- `Using C++ to reconstruct whole project with PCL`
- `Improve performance to real-time scenarios` 

## Dependencies
**Caution! The dependencies of this project is quite different from that of the origin!**
- `python 3.8`
- `tensorflow 2.4.1` 
- `pybind 11`
- `ros`

## Installation

1. Clone this repository.
2. Clone `pybind11` from [pybind11](https://github.com/pybind/pybind11).
```bash
$ cd utils/lib_cpp
$ git clone https://github.com/pybind/pybind11.git
```
3. Compile C++ module in utils/lib_cpp by running the following command.
```bash
$ mkdir build && cd build
$ cmake -DCMAKE_BUILD_TYPE=Release ..
$ make
```
4. copy the `lib_cpp.so` to root directory:
```bash
$ cp lib_cpp.so ../../../
```

5. Download the [pre_trained model](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/github/Livox_detection1.1_model.zip) and unzip it to the root directory.

## Run

### For sequence frame detection

Download the provided rosbags : [rosbag](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/github/livox_detection_v1.1_data.zip) and then

```bash
$ roscore

$ rviz -d ./config/show.rviz

$ python livox_rosdetection.py

$ rosbag play *.bag -r 0.1
```
The network inference time is around `24ms`, but the point cloud data preprocessing module takes a lot of time based on python. If you want to get a faster real time detection demo, you can modify the point cloud data preprocessing module with c++.

To play with your own rosbag, please change your rosbag topic to `/livox/lidar`.