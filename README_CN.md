![image](./imgs/hand.gif)
# <img src="./imgs/icon.jpg" width="48">DeepMosaics
这是一个通过深度学习自动的为图片/视频添加马赛克,或消除马赛克的项目.<br>它基于“语义分割”以及“图像翻译”.<br>

## 一些说明
代码暂不包含训练部分,训练方法我将在空闲时间给出.<br>
现在,代码已经支持基于[pix2pixHD](https://github.com/NVIDIA/pix2pixHD)训练出的模型,但网络仍在训练中,这将使得输出结果看起来更加清晰,"真实".<br>

## 如何运行
可以通过我们预编译好的二进制包或源代码运行.<br>

### 预编译的程序包
对于Windows用户,我们提供了包含GUI界面的免安装软件包.<br>
可以通过下面两种方式进行下载: [[Google Drive]](https://drive.google.com/open?id=1LTERcN33McoiztYEwBxMuRjjgxh4DEPs)  [[百度云,提取码1x0a]](https://pan.baidu.com/s/10rN3U3zd5TmfGpO_PEShqQ) <br>

![image](./imgs/GUI.png)<br>

注意事项:<br>
- 程序的运行要求在64位Windows操作系统,我仅在Windows10下运行过,其他版本暂未经过测试<br>
- 请根据需求选择合适的预训练模型进行测试<br>
- 运行时间取决于电脑性能,对于视频文件,我们建议可以先使用截图进行测试.<br>
- 如果输出的视频无法播放,这边建议您可以尝试[potplayer](https://daumpotplayer.com/download/).

### 通过源代码运行
#### 前提要求
- Linux, Mac OS, Windows
- Python 3.6+
- [ffmpeg 3.4](http://ffmpeg.org/)
- [Pytorch 1.0+](https://pytorch.org/)  [(Old version codes)](https://github.com/HypoX64/DeepMosaics/tree/Pytorch0.4)
- CPU or NVIDIA GPU + CUDA CuDNN<br>
#### Python依赖项
代码依赖于opencv-python以及 torchvision,可有通过pip install 进行安装.
#### 克隆源代码:
```bash
git clone https://github.com/HypoX64/DeepMosaics
cd DeepMosaics
```
#### 下载测试视频以及预训练模型
可以通过以下两种方法下载测试视频以及预训练模型,并将他们置于项目文件夹中.<br>
[[Google Drive]](https://drive.google.com/open?id=10nARsiZoZGcaKw40nQu9fJuRp1oeabPs)   [[百度云,提取码7thu]](https://pan.baidu.com/s/1IG4bdIiIC9PH9-oEyae5Sg) 

#### 简单的例子
* 为视频添加马赛克,例子中认为手是需要打码的区域 ,可以通过切换预训练模型切换自动打码区域(输出结果将储存到 './result')
```bash
python3 deepmosaic.py
```
* 将视频中的马赛克移除,对于不同的打码物体需要使用对应的预训练模型进行马赛克消除(输出结果将储存到  './result')
```bash
python3 deepmosaic.py --mode clean --model_path ./pretrained_models/clean_hands_unet_128.pth --media_path ./result/hands_test_AddMosaic.mp4
```
#### 更多的参数
如果想要测试其他的图片或视频,请参照以下文件输入参数.
[[options.py]](https://github.com/HypoX64/DeepMosaics/blob/master/options.py) <br>

## 鸣谢
代码大量的参考了以下项目:[[pytorch-CycleGAN-and-pix2pix]](https://github.com/junyanz/pytorch-CycleGAN-and-pix2pix) [[Pytorch-UNet]](https://github.com/milesial/Pytorch-UNet)[[pix2pixHD]](https://github.com/NVIDIA/pix2pixHD)..
