# SNPE_YOLOv5

## SNPE1 to SNPE2 Migration
* C API replaces C++ API; C++ API is no longer available
* DLC now supports int8, int32, uint32, and fp16
* Input and Const layers are folded into consuming ops
* SNPE2 now supports native integer types, including uint8, uint16, and uint32. Existing code handling quantized 8-bit tensors needs to be updated

## Model Workflow
![model_workflow](https://github.com/user-attachments/assets/fef15672-e7bd-4cdf-b15b-a1b5fc9b9fe3)
* Model Optimization: Quantization and Compression
* Why quantize a model?
  - To run on Hexagon DSP and improve performance
 
## Runtime
![runtime](https://github.com/user-attachments/assets/252a95d9-c14e-4d04-84c6-c7321fa2df11)
* CPU: Support 32-bit floating-point or 8-bit quantized execution
* GPU: Support hybrid (32-bit or 16-bit) or full 16-bit floating-point modes
* DSP: Support 8-bit quantized execution
* AIP: Support 8-bit quantized execution

## Model Config
* Class: 85 = 80 classes + 5 (x, y, width, height, bbox_score)

## Video Pipeline
### RTSP
RTSP -> uridecodebin -> queue -> qtivtransform -> capsfilter (RGB) -> appsink -> SaftyQueue (size = 25) -> output
### Webcam
Webcam -> v4l2src -> queue -> qtivtransform -> capsfilter (RGB) -> appsink -> SaftyQueue (size = 25) -> output
### Explanation
*  SaftyQueue with a fixed size of 25, aligned with the frame rate (FPS)

## Prerequisites
### Hardware
* Platform: QCS6490
  - CPU: Octa-Core Kyro 670 CPU
  - GPU: Qualcomm® Adreno™ 643
### Software  
* OS: Ubuntu 20.04
* SNPE SDK: v2.22.6.240515
* Develop framework: OpenCV-4.5.5
* Model: YOLOv5s.onnx
* Dependencies: gflags，json-glib-1.0，glib-2.0，spdlog-1.10.0，jsoncpp-1.7.4, fmt, spdlog

## SNPE SDK Installation
[SNPE SDK](https://www.qualcomm.com/developer/software/neural-processing-sdk-for-ai)

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

