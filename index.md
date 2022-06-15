# Dual Attention Network for Scene Segmentation - Group 16
In this blog, Duel Attention Network (DANet) will be explained, and a proposal for an architecture improvement will be given and evaluated. In 2019, Fu et al. published an article that introduces the DANet. The architecture is used for scene segmentation. This is a fundamental and challenging problem which involves segmenting different image regions with semantic categorious including things (e.g. building, grass, sky) and discrete objects (e.g. pedestrian, car, bicycle). The study can applied to applications in automatic driving, robot sensing and image editing. In order to effectively solve the task of scene segmentation. A distinction needs to be made effectivly distinguish between objects of similar appaerance. For instance, regions of 'road' and 'concrete' can be indistinhuishable. Likewise, the objects of 'cars' may often be affaetced by scales, occlusion and illumination. Therefore, it is required to enhance the disciminiative ability of feature representations at the pixel-level as well as  global level. This is precisecely what the DANet aims to accomplish, namely, they introducedarchitecture with nbopth a position and a channel; attention module. To capture both local and global information.  an architetcure with both 


## Network architecture
 The architecture is adaptively integrates local features with their global dependencies. Specifically, in the architecture they append
 
 % Talk about structure %

![Image](cv-architecture.png)
<!-- <p align="center">
<img src= cv-architecture.png/ width=70% height=70%>
</p> -->


## Architecture addition
% Talk about the addition we made %
## Dataset


## Results


## Discussion and Conclusion

% Conclude on the results / process overall
