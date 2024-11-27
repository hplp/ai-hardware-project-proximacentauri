[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/Buol6fpg)
[![Open in Codespaces](https://classroom.github.com/assets/launch-codespace-2972f46106e565e64193e422d61a12cf1da4916b45550586e14ef0a7c637dd04.svg)](https://classroom.github.com/open-in-codespaces?assignment_repo_id=16858568)
# AI_Hardware_Project Milestone_1

## Team Name:
Proxima Centauri

## Team Members:
- Nitya Mitnala
- Rithani Priyanga
- Vishnuvartthan

## Project Title:
```DrEYEve``` — Perception System for Autonomous Vehicles Using NVDLA 

## Project Description:
Autonomous Vehicles are gaining popularity in the world of cars, and self-driven cars are being desired across the globe. With automated driving becoming a plausible feature of the future, we hope to address a key feature that ensures safety and efficiency by detecting objects and obstacles on roads and helps with path planning for vehicles: visual perception. The most important feature that come into play to give a car 'eyes' that are useful is the capability to process images accurately and quickly. This requires a system with high computational power. Since this system is to be deployed in vehicles, a desirable feature is energy efficiency. With high computational power and energy efficiency being the prime target features for improvement, we propose to implement a visual perception system on the Open-source NVDLA platform, using the YOLOv5 object detection algorithm.

The main steps for implementation are as follows:
- Choose a pre-trained YOLOv5 model and implement it for the chosen dataset.
- Convert YOLOv5 to ONNX format.
- Optimize the model with TensorRT.
- Load optimized model onto NVDLA platform and run inference.
- Performance Tuning: Quantization and Profiling


## Model Identification and Initial Training:
For our approach towards the problem, we have started working with the open source code provided in [1]. In this paper, YOLOv3 was found to be the most accurate and fastest model for object detection. Due to this, we have run the YOLOv3 code for the dataset provided, and converted the model to ONNX format, to be deployed on the hardware.

We have also decided to use a more recent version of YOLO: YOLOv5. We have used the YOLOv5 model provided in [2] with the corresponding pretrained weights (trained on the COCO dataset). We have trained YOLOv5 on the dataset for 20 epochs. The model parameters and initial validation results are detailed in the given figure.
![image](https://github.com/user-attachments/assets/ae64314c-c512-48da-952e-f7fce90a3c32)

Using google colab, the YOLOv5 repository was cloned and the required dependencies were installed. A pretrained YOLOv5 model was loaded as the model and was converted to ONNX format. We then verified and visualised the ONNX export using the Netron tool. 
![image](https://github.com/user-attachments/assets/0484ee50-2e84-409f-a7b0-78570d45269a)


## Dataset:
We have chosen two datasets:
1. An augmented dataset created and provided through the research detailed in [1].
2. A dataset for pothole detection from Roboflow, formatted for YOLOv5 PyTorch. [3]

Thus far, the training has been done on the first dataset. We plan to run the model on the second datase also.

## Hardware Setup:

## Resources:
1. Rao, S., & Mitnala, N. (2023). Exploring automated object detection methods for manholes using classical computer vision and deep learning. Machine Graphics & Vision, 32(1).
2. https://github.com/ultralytics/yolov5.git
3. https://public.roboflow.com/object-detection/pothole/1
