# Object-Detection-and-location-RealsenseD435 and yolov3
## Requirements
Ubuntu18.04 OR 16.04  
[Opencv 4.x](https://github.com/opencv/opencv.git)  
C++ 11_std At least,I used the C++ 17 std  
Eigen3 :in absolutely Path /usr/local/eigen3  
Cmake>= 3.17  
PCL lib>=1.7.1  
[Intel Realsense SDK >=2.0 ](https://github.com/IntelRealSense/librealsense.git)  
Yolov3
## How to use
```Bash
git clone https://github.com/a1997-dom/Object-Detection-with-D435-and-yolov3.git
cd  Object-Detection-with-D435-and-yolov3/DNN/engine/
wget https://pjreddie.com/media/files/yolov3.weights ;wget https://pjreddie.com/media/files/yolov3-tiny.weights
```
you Can change the engine path in src/main.cpp   
on line 25-27
```cpp
String yolo_tiny_model ="../engine/yolov3.weights";
String yolo_tiny_cfg =  "../engine/yolov3.cfg";
String classname_path="../engine/coco.names";
``` 
You can use your weight by Darknet or others supported by DNN too  
```
cd ..
mkdir bulid; cd build
cmake ..
make
./DNN_Yolo
```
Attention:Default parameter on line 251 and 252 in src/main.cpp   
```cpp
    net.setPreferableBackend(DNN_BACKEND_OPENCV);// DNN_BACKEND_INFERENCE_ENGINE DNN_BACKEND_CUDA
    net.setPreferableTarget(DNN_TARGET_CPU);//DNN_TARGET_CUDA
```
if you have IntelCore CPU you can chose "DNN_BACKEND_INFERENCE_ENGINE"to accelerate youe model--Openvino;<br>
But you should make sure your CPU is Intel and the Contrib of Opencv has been installed.  
If you have GPU(From Nvidia),You can Think about The Cuda acceleration.Before this you should reinstall Your Opencv(Version Most>4.2) with This:[OpenCV_DNN](https://medium.com/@sb.jaduniv/how-to-install-opencv-4-2-0-with-cuda-10-1-on-ubuntu-20-04-lts-focal-fossa-bdc034109df3)  
Open the Cuda Setting when CMake.
