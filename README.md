# Physics-guided foundation model for universal speckle removal in ultrathin multimode fiber imaging (SCNet)

## Installation

This implementation is based on [BasicSR](https://github.com/xinntao/BasicSR) which is an open-source toolbox for image/video restoration tasks, [NAFNet](https://github.com/megvii-research/NAFNet), [Restormer](https://github.com/swz30/Restormer/tree/main/Denoising) and [CGNet](https://github.com/Ascend-Research/CascadedGaze).

```python
python 3.12.11
pytorch 2.8.0
cuda 12.8
```

```
pip install -r requirements.txt
```

## Quick Start 

We have provided ```test.py``` to show how to load images from the test dataset and use the model to restore images.

## SCNet implementation

The implementation of our proposed Speckle Clean Net can be found  in```/SCNet/basicsr/models/archs/SCNet_arch.py```

##  Speckle clean on gray image

### 1. Data Preparation
##### Place the train set in ```./datasets/train/```,
##### Place the evaluation data in ```./datasets/val/```,

**Place the test data in** **`./datasets/test/:`**



#### Dataset structure should be like this:

```
└── datasets/
    ├── train/
    │   ├── input
    │   │   ├── 1.PNG
    │   │   ├── 2.PNG
    │   │   ....
    │   └── target
    │       ├── 1.PNG
    │       ├── 2.PNG    
    ├── val/
    └── test/
        ├── input
        |   ├── 1.PNG
		|   ├── 2.PNG  
        └── target
            ├── 1.PNG
            ├── 2.PNG       
```

### 2. Training

* To train the SCNet model:

```
python basicsr/train.py -opt options/train.yml
```


### 3. Evaluation


#### Note: Due to the file size limitation, we are not able to share the pre-trained models in this code submission. However, they will be provided with an open-source release of the code.


##### Testing the model

  * To evaluate the pre-trained model use this file:
```
SCNet/basicsr/test.py
```

### 4. Model complexity and inference speed
* To get the parameter count, MAC, and inference speed use this file:
```
python SCNet/basicsr/models/archs/SCNet_arch.py
```

### Visualizing the training logs
* You can use Tensorboard to track the training status:
```
tensorboard --logdir=/SCNet/logs
```

# Related Works

#### **Thank CGNet and NAFNet for providing us with excellent ideas through their work !**

- **CascadedGaze: Efficiency in Global Context Extraction for Image Restoration, NeurIPS 2024.**

  [Paper]([[2401.15235\] CascadedGaze: Efficiency in Global Context Extraction for Image Restoration](https://arxiv.org/abs/2401.15235)) | [Code](https://github.com/Ascend-Research/CascadedGaze)

- **NAFNet: Nonlinear Activation Free Network for Image Restoration, ECCV 2022.**

  [Paper]([[2204.04676\] Simple Baselines for Image Restoration](https://arxiv.org/abs/2204.04676)) | [Code](https://github.com/megvii-research/NAFNet)
