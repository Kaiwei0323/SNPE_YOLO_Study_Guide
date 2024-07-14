# SNPE_YOLOv5

## Prerequisites
* Hardware Platform: QCS6490
* OS: Ubuntu 18.04
* SNPE SDK: snpe-2.5.0.4052
* Develop framework: OpenCV-4.5.5
* Model: YOLOv5s.onnx
* Additional Package: FMT, 

## Enter Admin
```
su
oelinux123
```

## Package Installation
```
apt update
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
cd spdlog && mkdir build && cd build
cmake .. && make -j
cd ..
cp -r include/spdlog /usr/local/include
${PROJECT_SOURCE_DIR}/include/spdlog
```

## jsoncpp Installation
```
git clone https://github.com/open-source-parsers/jsoncpp.git
cd jsoncpp
mkdir build
cd build
cmake ..
make install
```
https://stackoverflow.com/questions/36861355/fatal-error-with-jsoncpp-while-compiling

## meson installation
```
git clone https://github.com/mesonbuild/meson.git
cd meson
python3 setup.py install
```

## ninja Installation
```
git clone https://github.com/ninja-build/ninja.git
cd ninja
./configure.py --bootstrap
cp ninja /usr/local/bin/
```

## gobject-introspection-1.0 Installation
```
git clone https://gitlab.gnome.org/GNOME/gobject-introspection.git
meson setup _build .
meson compile -C _build
meson test -C _build
meson install -C _build
```

## json-glib Installation
```
git clone https://gitlab.gnome.org/GNOME/json-glib.git
meson setup _build -Dintrospection=disabled
meson compile -C _build
meson test -C _build
meson install -C _build
```

