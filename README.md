# SNPE_YOLOv5

## Prerequisites
* Hardware Platform: QCS6490
* OS: Ubuntu 18.04
* SNPE SDK: snpe-2.5.0.4052
* Develop framework: OpenCV-4.5.5
* Model: YOLOv5s.onnx
* Dependencies: gflags，json-glib-1.0，glib-2.0，spdlog-1.10.0，jsoncpp-1.7.4，mosquitto，mosquitto-clients
* Additional Packages: fmt, spdlog 

## Enter Admin mode
```
su
oelinux123
```

## Package Installation
```
apt install git
git clone https://github.com/gesanqiu/SNPE_Tutorial.git
```

## OpenCV Installation
```
apt install build-essential cmake git pkg-config libgtk-3-dev \
                 libavcodec-dev libavformat-dev libswscale-dev libv4l-dev \
                 libxvidcore-dev libx264-dev libjpeg-dev libpng-dev \
                 libtiff-dev gfortran openexr libatlas-base-dev \
                 python3-dev python3-numpy libtbb2 libtbb-dev \
                 libdc1394-22-dev libeigen3-dev libopenblas-dev \
                 liblapack-dev libavresample-dev libgstreamer1.0-dev \
                 libgstreamer-plugins-base1.0-dev libgoogle-glog-dev \
                 libprotobuf-dev protobuf-compiler libprotoc-dev \
                 libgoogle-glog-dev libgflags-dev libgphoto2-dev \
                 libhdf5-dev
```
```
mkdir ~/opencv_build
cd ~/opencv_build
git clone --branch 4.5.5 https://github.com/opencv/opencv.git
git clone --branch 4.5.5 https://github.com/opencv/opencv_contrib.git
```
```
cmake -D CMAKE_BUILD_TYPE=RELEASE \
      -D CMAKE_INSTALL_PREFIX=/usr/local \
      -D OPENCV_EXTRA_MODULES_PATH=~/opencv_build/opencv_contrib/modules \
      -D ENABLE_NEON=ON \
      -D WITH_OPENMP=ON \
      -D WITH_OPENGL=ON \
      -D WITH_TBB=ON \
      -D BUILD_TBB=ON \
      -D BUILD_TESTS=OFF \
      -D INSTALL_PYTHON_EXAMPLES=OFF \
      -D OPENCV_ENABLE_NONFREE=ON \
      -D BUILD_EXAMPLES=OFF \
      ~/opencv_build/opencv
```
```
make -j$(nproc)
make install
```

## SNPE SDK Installation
```
https://developer.qualcomm.com/downloads/qualcomm-neural-processing-sdk-linux-v2050
```

## Python 3.6 Installation
```
wget https://www.python.org/ftp/python/3.6.15/Python-3.6.15.tgz
tar -xf Python-3.6.15
cd Python-3.6.15
./configure --prefix=/usr/local --enable-optimizations
make
make install
```

## Dependencies Installation
```
apt-get install libjson-glib-dev libgflags-dev libjsoncpp-dev libmosquitto-dev mosquitto mosquitto-clients
```

## FMT Installation
```
git clone https://github.com/fmtlib/fmt.git
cd fmt
mkdir build
cd build
cmake ..
make -j$(nproc)
make install
```

## spdlog Installation
```
git clone https://github.com/gabime/spdlog.git
cd spdlog
mkdir build
cd build
cmake ..
make -j$(nproc)
make install
```

## Image Detection
```
./test/test_image/test-image --input ../test/test_image/people.jpg --labels ../model/yolov5s_labels.txt --config_path ../test/test_image/config.json
```

## Video Detection
```
./test/test_video/test-video --config_path ../test/test_video/config.json
```
```
mosquitto_sub -t test-topic
```

## Reference
```
https://docs.qualcomm.com/bundle/publicresource/topics/80-70014-254/introduction.html
```
```
https://docs.qualcomm.com/bundle/publicresource/topics/80-70014-17/using_gst_launch_1_0.html
```

