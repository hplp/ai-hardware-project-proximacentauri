[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/Buol6fpg)
[![Open in Codespaces](https://classroom.github.com/assets/launch-codespace-2972f46106e565e64193e422d61a12cf1da4916b45550586e14ef0a7c637dd04.svg)](https://classroom.github.com/open-in-codespaces?assignment_repo_id=16858568)
# AI_Hardware_Project Miledtone_1

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


## Key Objectives:
- Implementation of YOLOv5 algorithm on NVDLA
- Improving Computation 
- Memory improvements
- Improving energy efficiency

## Technology Stack:
- Platform: NVDLA
  ![image](https://github.com/user-attachments/assets/4159eab1-7069-4d1e-b506-3d6ce37654ff)
- Supporting Software: Ubuntu to run the NVDLA platform and other supporting drivers
- Software: YOLOv5
- Languages: Python, verilog, systemC
- Datasets:
  - Primary: Geomatics and Computer Vision (road level images of drains and manholes)
  - Secondary: BDD100K (used for finding drivable space on the road), Cityscapes (semantically segmented data of urban areas)

## Expected Outcomes:
Have a YOLOv5 based model that 
- is based on NVDLA
- is energy efficient
- has the capability to detect objects on the road real-time
- can be deployed on an autonomous vehicle.

## Timeline:
Week 1:	Dataset preparation, initial training of YOLOv5 on dataset.
Week 2:	Model optimization with TensorRT and conversion to ONNX.
Week 3:	Apply quantization, configure NVDLA platform, load optimized model, run  initial performance tests.
Week 4:	Optimization for energy efficiency and parallel processing, final validation, documentation.
