# computerVision2022

## Introduction
NeRF is an algorithm for representing a realistic volumetric scene using a fully-connected deep neural network called MLP. NeRF is known as one of the most influential work in 3D vision field due to its advantages on high-resolution output and storage space. 
 However, editing NeRF is an extremely challenging task. Since NeRF has an implicit function optimized per scene, we cannot directly edit its shape. Moreover, the final output is too strongly connected to the input images, it is hard to change the output’s light direction or color. This multi-view dependency of NeRF makes the modification of its output more complicate. 
For these reasons, we aimed at manipulation of NeRF’s 3D output. We introduced the new way of editing the object color and the location of light source, through the RGB map information of naive NeRF. As a result, we’ve shown that our method could effectively generate the modification version of NeRF’s output. Furthermore, we achieved the optimization of overall calculation and reduced our rendering time successfully. 

## Overall pipeline
Before starting the concrete explanation about our implementation, we would introduce the overall pipeline and NeRF’s basic dataset analysis. Since our project is focused on the modification of the NeRF network’s output, it is also important to understand NeRF correctly. 
In original NeRF, the pre-trained network takes camera pose as an input and generates the RGB and depth map as output. Using that information, NeRF renders the 2D image which represents the target 3D object. 
In our project, we first trained the original NeRF with the 3D objects we intended. And we appended the new RGB function right before the rendering process, to handle the NeRF’s RGB map. For this, we additionally gave the light direction and object’s color information as the arguments of our RGB function. After the whole re-calculation of RGB map, we could finally get the manipulated output we wanted. 


## Implementation 
To find the implementation part of our project, notice the `change_color()` function in the `run_nerf.py` file.
