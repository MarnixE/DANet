# Dual Attention Network for Scene Segmentation - Group 16
In this blog, Duel Attention Network (DANet) will be explained, and a proposal for an architecture improvement will be given and evaluated. In 2019, Fu et al. published an article that introduces the DANet. An architecture is build upon the Pytorch Encoding


Unlike previous works that cap-
ture contexts by multi-scale feature fusion, we propose a
Dual Attention Network (DANet) to adaptively integrate lo-
cal features with their global dependencies. Specifically,
we append two types of attention modules on top of dilated
FCN, which model the semantic interdependencies in spa-
tial and channel dimensions respectively. The position at-
tention module selectively aggregates the feature at each
position by a weighted sum of the features at all positions.
Similar features would be related to each other regardless
of their distances. Meanwhile, the channel attention mod-
ule selectively emphasizes interdependent channel maps by
integrating associated features among all channel maps.
We sum the outputs of the two attention modules to further
improve feature representation which contributes to more
precise segmentation results. We achieve new state-of-the-
art segmentation performance on three challenging scene
segmentation datasets, i.e., Cityscapes, PASCAL Context
and COCO Stuff dataset. In particular, a Mean IoU score
of 81.5% on Cityscapes test set is achieved without using
coarse data.1.

## Network architecture


## Architecture addition


## Results


## Conclusion
