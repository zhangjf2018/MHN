## Code for ICCV 2019 Paper "[Mixed High-Order Attention Network for Person Re-Identification](http://bhchen.cn)"

This code is developed based on pytorch framework and the [baseline](https://github.com/layumi/Person_reID_baseline_pytorch) code.

* [Updates](#updates)
* [Files](#files)
* [Prerequisites](#prerequisites)
* [Train_Model](#train_model)
* [Evaluation](#evaluation)
* [Contact](#contact)
* [Citation](#citation)
* [LICENSE](#license)

### Updates
- Aug 16, 2019
  * The codes of training and testing for our [ICCV19 paper](http://bhchen.cn) are released.
  * We have cleared up and tested the codes on Market, Duke datasets, the expected retrieval performances are as follows:
  
  |Market | R@1 | R@5| R@10 | mAP | Reference |
  | -------- | ----- | ---- | ---- | ---- | ---- |
  | IDE+ERA | 89.9% | 96.4%| 97.6%| 75.6%|  `train_ide.py` |
  | IDE+MHN6 | 93.1%|97.7% |98.7%| 83.2% | `train_ide.py` |
  | PCB+ERA | 91.7%| 97.4%| 98.3%| 76.4% | `train_smallPCB` |
  | PCB+MHN4 | 94.3%| 98.0%| 98.8%| 83.9% | `train_smallPCB` |
  | PCB+MHN6 | 94.8%| 98.3%| 98.9%| 85.2% | `train_smallPCB_multiGPU.py` |
  
  |Duke | R@1 | R@5| R@10 | mAP | Reference |
  | -------- | ----- | ---- | ---- | ---- | ---- |
  | IDE+ERA | 82.7% |91.8%| 94.1%| 68.1%|  `train_ide.py` |
  | IDE+MHN6 | 87.8% |94.2%| 95.8%| 74.6% | `train_ide.py` |
  | PCB+ERA | 82.9%| 91.7%| 93.8%| 67.7% | `train_smallPCB` |
  | PCB+MHN4 | 88.5%| 94.5%| 96.1%| 76.9% | `train_smallPCB` |
  | PCB+MHN6 | 89.5%| 94.7%| 96.1%| 77.5% | `train_smallPCB_multiGPU.py` |

### Files
- train_ide.py test_ide.py
  * files for training and testing on IDE framework

- train_smallPCB.py test_smallPCB.py
  * files for training and testing on PCB framework, when using MHN, the maximized order is limited to 4 due to the GPU memory.

- train_smallPCB_multiGPU.py test_smallPCB.py
  * files for training, if you want to test MHN6, please use this file for training with multi gpus. The testing file is also test_smallPCB.py

- auto_test.sh
  * sh testing code.
### Prerequisites
* Pytorch(0.4.0+)
* python3.6
* 2GPUs, each > 11G
### Train_Model
1. Clone our code.
2. Download the training images {[google drive](https://drive.google.com/file/d/1X6JB2Cm4kMlwor5GjGS9vXKK9rIgTTDT/view?usp=sharing), [baidu](https://pan.baidu.com/s/1-A_Ibc2sWKV85nCwJp0kKA)}, including **Market1501, DukeMTMC, CUHK03-NP**.
3. Go into the MHN/ dir and mkdir datasets/, then unzip the downloaded datasets.zip to datasets/
4. Run prepare.py to preprocess the datasets.
5. Then you can try our methods

```
        cd ~/Hybrid-Attention-based-Decoupled-Metric-Learning-master/examples/CUB/U512
        ./finetune_U512.sh
```     
and
```
        cd ~/Hybrid-Attention-based-Decoupled-Metric-Learning-master/examples/CUB/DeML3-3_512
        ./finetune_DeML3-3_512.sh
```     
the trained models are stored in folder "run_U512/" and "run_DeML3-3_512/" respectively.
### Extract_DeepFeature
1. run the following code for **U512** and **DeML(I=3,J=3)** respectively.
```
        cd ~/Hybrid-Attention-based-Decoupled-Metric-Learning-master/examples/CUB/U512
        ./extractfeatures.sh
```

```
        cd ~/Hybrid-Attention-based-Decoupled-Metric-Learning-master/examples/CUB/DeML3-3_512
        ./extractfeatures.sh
```
the feature files are stored at folder "features/"
### Evaluation
1. Run code in folder "~/Hybrid-Attention-based-Decoupled-Metric-Learning-master/evaluation/"
### Contact 
- [Binghui Chen](http://bhchen.cn)

### Citation
You are encouraged to cite the following papers if this work helps your research. 

    @inproceedings{chen2019hybrid,
      title={Hybrid-Attention based Decoupled metric Learning for Zero-Shot Image Retrieval},
      author={Chen, Binghui and Deng, Weihong},
      booktitle={Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition (CVPR)},
      year={2019},
    }
    @InProceedings{chen2019energy,
    author = {Chen, Binghui and Deng, Weihong},
    title = {Energy Confused Adversarial Metric Learning for Zero-Shot Image Retrieval and Clustering},
    booktitle = {AAAI Conference on Artificial Intelligence},
    year = {2019}
    }
### License
Copyright (c) Binghui Chen

All rights reserved.

MIT License

Permission is hereby granted, free of charge, to any person obtaining a
copy of this software and associated documentation files (the "Software"),
to deal in the Software without restriction, including without limitation
the rights to use, copy, modify, merge, publish, distribute, sublicense,
and/or sell copies of the Software, and to permit persons to whom the
Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included
in all copies or substantial portions of the Software.


