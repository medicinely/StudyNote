# Linux命令

## CUDA、CuDNN及Pytorch、Tensorflow安装

1. 安装NVIDIA显卡驱动

   Software&Updates - Additional Driver -重启

2. 安装cuda-toolkit

   ```commonlisp
   conda install -c anaconda cudatoolkit
   ```

3. 安装cuDNN

   ```
   conda install -c anaconda cudnn
   ```

4. [安装pytorch](https://pytorch.org/get-started/locally/)

   ```
   conda install pytorch torchvision torchaudio cudatoolkit=10.1 -c pytorch
   ```

   [安装tensorflow](https://www.tensorflow.org/install/gpu?hl=zh-cn)

   ```
   pip install tensorflow
   ```
5. 安装opencv
   ```
   pip install opencv-python
   ```

6. 查看cuda版本

   ```
   nvcc --version
   ```

   查看pytorch版本

   ```
   torch.__version__
   ```

   查看显卡运行状态

   ```
   nvidia-smi -l t
   ```

   检查pytorch是否已支持显卡

   ```python
   import torch
   torch.cuda.is_available()
   torch.cuda.get_device_name(0)
   ```

   检查tensorflow是否已支持显卡

   ```python
   import tensorflow as tf
   tf.test.gpu_device_name() 
   tf.test.is_gpu_available()
   ```



## Detectron2 demo

### 预测图像：

```
python demo.py --config-file ../configs/COCO-InstanceSegmentation/mask_rcnn_R_50_FPN_3x.yaml --input input.jpg --opts MODEL.WEIGHTS detectron2://COCO-InstanceSegmentation/mask_rcnn_R_50_FPN_3x/137849600/model_final_f10217.pkl
```

### 预测视频：

```
python demo.py --config-file ../configs/COCO-InstanceSegmentation/mask_rcnn_R_50_FPN_3x.yaml --video-input hongkong.mp4 --opts MODEL.WEIGHTS detectron2://COCO-InstanceSegmentation/mask_rcnn_R_50_FPN_3x/137849600/model_final_f10217.pkl
```

### 保存视频：

```
python demo.py --config-file ../configs/COCO-InstanceSegmentation/mask_rcnn_R_50_FPN_3x.yaml --video-input hongkong.mp4  --output hongkong_output --opts MODEL.WEIGHTS detectron2://COCO-InstanceSegmentation/mask_rcnn_R_50_FPN_3x/137849600/model_final_f10217.pkl
```





















































