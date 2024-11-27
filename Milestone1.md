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
`DrEYEve` — Perception System for Autonomous Vehicles Using NVDLA 

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

We have also decided to use a more recent version of YOLO: YOLOv5. We have used the YOLOv5 model provided in [2] with the corresponding pretrained weights (trained on the COCO dataset). We have trained YOLOv5 on the first dataset for 20 epochs and on the second dataset for 100 epochs. The model parameters and initial validation results are detailed in the given figures:

Dataset 1:
![image](https://github.com/user-attachments/assets/ae64314c-c512-48da-952e-f7fce90a3c32)

Dataset 2:
![image](https://github.com/user-attachments/assets/356441b2-7ac2-4ec2-91bc-cd18a2e334b1)



Using google colab, the YOLOv5 repository was cloned and the required dependencies were installed. A pretrained YOLOv5 model was loaded as the model and was converted to ONNX format. We then verified and visualized the ONNX export using the Netron tool. The image gives us a visualization of the computational graph of the YOLOv5 model and represents the structure of the neural network - comprising of the layers, operations and connections.

![image](https://github.com/user-attachments/assets/0484ee50-2e84-409f-a7b0-78570d45269a)

The input node represents the input tensor to the model with dimensions - (batch_size, channels - 3, height - 640, width - 640). The convolutional layers are used for feature extraction and the layers apply filters to the input data followed by activation function. These convolutional layers are followed by batch normalization ('BatchNorm') layers to normalize the output and improve training stability. To introduce non-linearity into the model - the SiLU activation functions are applied after certain layers. The YOLOv5 uses residual connections which makes the gradients flow easily during backpropagation and are reflected as branching paths in the graph. The multiple branches that merge features from different scales are the multi-scale feature detection used by YOLOv5 (Feature Pyramid Network). At the bottom of the graph the detection heads are visible which are responsible for generating predictions (bounding boxes, objectness scores and class probabilities) and these heads map to different scales (small, medium. large objects). 

## Dataset:
We have chosen two datasets:
1. An augmented dataset created and provided through the research detailed in [1].
2. A dataset for pothole detection from Roboflow, formatted for YOLOv5 PyTorch. [3]

## NVDLA Setup (Open source platform):
To set up the NVDLA platform, refer to the detailed guide provided on the [NVDLA VP setup page](https://nvdla.org/vp.html#using-the-virtual-simulator). Follow the instructions to configure the virtual simulator, ensuring all dependencies and environment settings are correctly implemented.

It is required to install the platform on Ubuntu 14.04 to ensure that only the compatible versions of all dependencies are installed, as the virtual simulator supports only specific versions and not the latest ones.

#### Downloading the Virtual Simulator
```
git clone https://github.com/nvdla/vp.git
cd vp
git submodule update --init --recursive
```
Errors may occur when updating submodules using the command. This can happen for two reasons: (1) some URLs referenced in the submodules may no longer be in use, and (2) the `git://` protocol does not function behind a firewall. To resolve these issues, the `git://` protocol in the `.../vp/libs/qbox/.gitmodules` file should be replaced with `https://`. The corrected `.gitmodules` file is available at [/qbox/.gitmodules](https://github.com/hplp/ai-hardware-project-proximacentauri/blob/main/qbox/.gitmodules). Replacing the original file with this version will address the errors.

#### Install the dependencies
All necessary dependencies from Section 2.3 of the setup documentation page must be installed. Also, install Verilator and Clang.
```
sudo apt install verilator clang
```
During the build process for NVDLA CMOD, a name for the hw project, paths for the installed dependencies such as g++, cpp, perl, java, systemc, verilator and clang must be provided. Verification of the paths can be performed as below:
```
which cpp
```
When the NVDLA HW is successfully built, header files and libraries will be generated in the `.../hw/outdir/[project name]/cmod` directory.

Finally, in the VP repository directory, the following command builds the virtual simulator:
```
cmake -DCMAKE_INSTALL_PREFIX=[install dir] -DSYSTEMC_PREFIX=[systemc prefix] -DNVDLA_HW_PREFIX=[nvdla_hw prefix] -DNVDLA_HW_PROJECT=[nvdla_hw project name]`
```
- *[install dir]*: Directory to install the virtual simulator.
- *[systemc prefix]*: Path where SystemC is installed (e.g., /usr/local/systemc-2.3.0/).
- *[nvdla_hw prefix]*: Directory where the NVDLA HW repository is cloned (e.g., /home/<username>/hw).
- *[nvdla_hw project name]*: The project name used during the HW build.

```
make
make install
```


## Resources:
1. Rao, S., & Mitnala, N. (2023). Exploring automated object detection methods for manholes using classical computer vision and deep learning. Machine Graphics & Vision, 32(1).
2. https://github.com/ultralytics/yolov5.git
3. https://public.roboflow.com/object-detection/pothole/1
4. https://nvdla.org/vp.html
