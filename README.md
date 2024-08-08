# SNPE_YOLOv5

## Prerequisites
* Hardware Platform: QCS6490
* OS: Ubuntu 20.04
* SNPE SDK: v2.22.6.240515
* Develop framework: OpenCV-4.5.5
* Model: YOLOv5s.onnx
* Dependencies: gflags，json-glib-1.0，glib-2.0，spdlog-1.10.0，jsoncpp-1.7.4, fmt, spdlog

## SNPE SDK Installation
```
[SNPE SDK](https://www.qualcomm.com/developer/software/neural-processing-sdk-for-ai)
```

## Enter Admin mode
```
su
Password: oelinux123
```

## OpenCV Installation
```
./install_opencv.sh
```

## Dependencies Installation
```
./install_dependencies.sh
```

## Build and Installation
### 1. Modify SNPE Library Directory in CMake file
* set(SNPE_INCLUDE_DIR /home/aim/Documents/v2.22.6.240515/qairt/2.22.6.240515/include/SNPE)
* set(SNPE_LIBRARY_DIR /home/aim/Documents/v2.22.6.240515/qairt/2.22.6.240515/lib/aarch64-ubuntu-gcc9.4)

### 2. Build Application
```
./build_app.sh
```

## Video Inference
```
./video_inference.sh
```

## Webcam Inference
```
./webcam_inference.sh
```

