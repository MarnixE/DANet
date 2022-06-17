# [Clustering Extension for Dual Attention Network for Scene Segmentation(CVPR2019)](https://arxiv.org/pdf/1809.02983.pdf)

## Introduction

We propose an extension to Dual Attention Network (DANet) by adding a clustering layer before the attention modules (the clustering layer follows the implementation found at https://github.com/mlpc-ucsd/ConstellationNet). 

## Usage
You can either follow the steps below or use this [notebook](https://colab.research.google.com/drive/15aPxvooFAtEccKZvI9HqYlyjASYzrSyd?usp=sharing) as reference.

1. Install pytorch 

   - The code is tested on python3.6 and torch 1.4.0.
   - The code is modified from [PyTorch-Encoding](https://github.com/zhanghang1989/PyTorch-Encoding). 

2. Clone the resposity

   ```shell
   git clone https://github.com/MarnixE/DANet.git 
   cd DANet 
   python setup.py install
   ```

3. Dataset
   - Download the dataset you are more intrested in. We tested PASCAL VOC 2012.

4. Train for ClusterDANet

   - `cd ./experiments/segmentation/`
   - 
   - ```shell
     CUDA_VISIBLE_DEVICES=0,1,2,3 python train.py --dataset pascal_voc --model clusterdanet --backbone resnet101 --checkname clusterdanet_test --base-size 520 --crop-size 480 --epochs 22 --batch-size 4 --lr 0.003
     ```

5. Evaluation for ClusterDANet

   - Move the model generated at training in a models folder and then you can test the model. 

   - ```shell
     CUDA_VISIBLE_DEVICES=0,1,2,3 python test.py --dataset pascal_voc --model clusterdanet --backbone resnet101 --resume  models/clusterdanet_test.pth.tar --eval --base-size 520 --crop-size 480
     ```
