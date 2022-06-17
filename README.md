# [Clustering Extension for Dual Attention Network for Scene Segmentation(CVPR2019)](https://arxiv.org/pdf/1809.02983.pdf)

## Introduction

We propose an extension to Dual Attention Network (DANet) by adding a clustering layer before the attention modules.

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

   - Download trained model [DANet101](https://drive.google.com/open?id=1XmpFEF-tbPH0Rmv4eKRxYJngr3pTbj6p) and put it in folder `./experiments/segmentation/models/`

   - `cd ./experiments/segmentation/`

   - For single scale testing, please run:

   - ```shell
     CUDA_VISIBLE_DEVICES=0,1,2,3 python test.py --dataset citys --model danet --backbone resnet101 --resume  models/DANet101.pth.tar --eval --base-size 2048 --crop-size 768 --workers 1 --multi-grid --multi-dilation 4 8 16 --os 8 --aux --no-deepstem
     ```

   - Evaluation Result

     The expected scores will show as follows: DANet101 on cityscapes val set (mIoU/pAcc): **79.93/95.97**(ss) 

5. Evaluation for DRANet

   - Download trained model [DRANet101](https://drive.google.com/file/d/1xCl2N0b0rVFH4y30HCGfy7RY3-ars7Ce/view?usp=sharing) and put it in folder `./experiments/segmentation/models/`

   - Evaluation code is in folder `./experiments/segmentation/`

   - `cd ./experiments/segmentation/`

   - For single scale testing, please run:

   - ```shell
     CUDA_VISIBLE_DEVICES=0,1,2,3 python test.py --dataset citys --model dran --backbone resnet101 --resume  models/dran101.pth.tar --eval --base-size 2048 --crop-size 768 --workers 1 --multi-grid --multi-dilation 4 8 16 --os 8 --aux
     ```

   - Evaluation Result

     The expected scores will show as follows: DRANet101 on cityscapes val set (mIoU/pAcc): **81.63/96.62** (ss) 

## Citation

if you find DANet and DRANet useful in your research, please consider citing:

```
@article{fu2020scene,
  title={Scene Segmentation With Dual Relation-Aware Attention Network},
  author={Fu, Jun and Liu, Jing and Jiang, Jie and Li, Yong and Bao, Yongjun and Lu, Hanqing},
  journal={IEEE Transactions on Neural Networks and Learning Systems},
  year={2020},
  publisher={IEEE}
}
```

```
@inproceedings{fu2019dual,
  title={Dual attention network for scene segmentation},
  author={Fu, Jun and Liu, Jing and Tian, Haijie and Li, Yong and Bao, Yongjun and Fang, Zhiwei and Lu, Hanqing},
  booktitle={Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition},
  pages={3146--3154},
  year={2019}
}
```



References:

</h3>

[1]: **Martins, Ines Filipa, et al.** (2012). [A Bayesian approach to
    in silico blood-brain barrier penetration
    chemical information and modeling 52.6, 1686-1697

[2]: **van der Maaten, Laurens, Hinton, Geoffrey.** (2008).
    [Viualizingdata using
    t-SNE.](https://www.jmlr.org/papers/volume9/vandermaaten08a/vandermaaten08a.pdf?fbclid=IwAR0Bgg1eA5TFmqOZeCQXsIoL6PKrVXUFaskUKtg6yBhVXAFFvZA6yQiYx-M)
    Journal of Machine Learning Research. 9. 2579-2605.
