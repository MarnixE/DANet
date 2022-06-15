# Dual Attention Network for Scene Segmentation - Group 16
In this blog, Duel Attention Network (DANet) will be explained, and a proposal for an architecture improvement will be given and evaluated. In 2019, Fu et al. published an article that introduces the DANet. The architecture is used for scene segmentation. This is a fundamental and challenging problem which involves segmenting different image regions with semantic categorious including things (e.g. building, grass, sky) and discrete objects (e.g. pedestrian, car, bicycle). The study can applied to applications in automatic driving, robot sensing and image editing. In order to effectively solve the task of scene segmentation. A distinction needs to be made effectivly distinguish between objects of similar appaerance. For instance, regions of 'road' and 'concrete' can be indistinhuishable. Likewise, the objects of 'cars' may often be affacted by scales, occlusion and illumination. Therefore, it is required to enhance the disciminiative ability of feature representations at the pixel-level as well as  global level. This is precisecely what the DANet aims to accomplish. Namely, they introduced an architecture with both a position and a channel attention module, to capture both local and global information.


## Network architecture
 The architecture is adaptively integrates local features with their global dependencies. Specifically, in the architecture they append
 
 % Talk about structure %

![Image](cv-architecture.png)
<!-- <p align="center">
<img src= cv-architecture.png/ width=70% height=70%>
</p> -->


## Architecture addition
To increase the performance of the architecture we wanted to add clustering layers before the 
self-attention layers. This idea was based on a paper by Xu et al. Here they implement cell feature clustering. Where cell features are defined as individual local feature at a position in the feature map. By clustering these cell features they are able to model the underlying distribution of input cell features. Through this method, the authors were able to bring 2.5-6.4% performance increase over baseline models. 

The method employed by the authors and for this project works by clustering individual features at each location in the feature map (i.e. cell features) into multiple centres and employing the cluster centres as filters. This is done using a mini-batch soft k-means algorithm to cluster the cell features approximately:

-	**Initialization.** Randomly initialize global cluster centers <img src="https://render.githubusercontent.com/render/math?math=\mathcal{V}=\left\{\mathbf{v}_{1}, \mathbf{v}_{2}, \ldots, \mathbf{v}_{K}\right\}"> and a counter <img src="https://render.githubusercontent.com/render/math?math=\mathbf{s}=\left(s_{1}, s_{2}, \ldots, s_{K}\right)=\mathbf{0}">.
-	**Cluster assignment.** In the forward step, given input cell features <img src="https://render.githubusercontent.com/render/math?math=\mathcal{U}=\left\{\mathbf{u}_{1}, \mathbf{u}_{2}, \ldots, \mathbf{u}_{n}\right\}">, we compute the distance vector <img src="https://render.githubusercontent.com/render/math?math=\mathbf{d}_{i}=\left(d_{i 1}, d_{i 2}, \ldots d_{i K}\right)"> between input cell feature <img src="https://render.githubusercontent.com/render/math?math=\mathbf{u_i}"> and all cluster centers <img src="https://render.githubusercontent.com/render/math?math=\mathcal{V}">. We can then compute the soft assignment <img src="https://render.githubusercontent.com/render/math?math=m_{i k} \in \mathbb{R}"> using the softmax function. This will be used to generate the mini-batch centers $v'_k$:

<!-- $$d_{i k}=\left\|\mathbf{u}_{i}-\mathbf{v}_{k}\right\|_{2}^{2}, \quad m_{i k}=\frac{e^{-\beta d_{i k}}}{\sum_{j} e^{-\beta d_{i j}}}, \quad \mathbf{v}_{k}^{\prime}=\frac{\sum_{i} m_{i k} \mathbf{u}_{i}}{\sum_{i} m_{i k}}$$ -->
<img src="https://render.githubusercontent.com/render/math?math=d_{i k}=\left\|\mathbf{u}_{i}-\mathbf{v}_{k}\right\|_{2}^{2}, \quad m_{i k}=\frac{e^{-\beta d_{i k}}}{\sum_{j} e^{-\beta d_{i j}}}, \quad \mathbf{v}_{k}^{\prime}=\frac{\sum_{i} m_{i k} \mathbf{u}_{i}}{\sum_{i} m_{i k}}">

- **Centroid Movement.** In the equation below we formalate $\Delta \mathrm{s}=\sum_{i} \mathbf{m}_{i}$ by summing all maps $\mathbf{m}_{i}=\left(m_{i 1}, m_{i 2}, \ldots m_{i K}\right)$. The mini-batch centers $v'_k$ are then updated to the global center $v_k$ with a momentum coefficient $\eta$.

<!-- $$
\mathbf{v}_{k} \leftarrow(1-\eta) \mathbf{v}_{k}+\eta \mathbf{v}_{k}^{\prime}, \quad \eta=\frac{\lambda}{s_{k}+\Delta s_{k}}
$$ -->
<img src="https://render.githubusercontent.com/render/math?math=\mathbf{v}_{k} \leftarrow(1-\eta) \mathbf{v}_{k}+\eta \mathbf{v}_{k}^{\prime}, \quad \eta=\frac{\lambda}{s_{k}+\Delta s_{k}}">

- **Counter Update.** Lastly a counter update $\mathbf{s}$ is updated and the distance vectors {$\mathbf{d_i}$} are reshaped and returned.

$$\mathbf{s} \leftarrow \mathbf{s} + \Delta \mathbf{s}$$

The above clustering algorthim is used for both attention layers in the DANet architecture. Which results in the following new architecture:

![Image](improved-architecture.png)
<!-- <p align="center">
<img src= improved-architecture.png/ width=70% height=70%>
</p> -->


## Dataset
The dataset used was PASCAL Visual Object Classes (VOC) dataset.  The PASCAL Visual Object Classes (VOC) 2012 dataset contains 20 object categories including vehicles, household, animals, and some others. Every image in this dataset has pixel-level segmentation annotations, bounding box annotations, and object class annotations. This dataset has been widely used as a benchmark for object detection, semantic segmentation, and classification tasks. The PASCAL VOC dataset is split into three subsets: 1,464 images for training, 1,449 images for validation and a private testing set. The Dual Attention Network for Scene Segmentation model on which our model is based on uses Cityscapes, PASCAL VOC 2012, PASCAL Context, COCO Stuff datasets.

## Results


## Discussion and Conclusion

% Conclude on the results / process overall
