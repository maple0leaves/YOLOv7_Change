# YOLOv7_Change
修改yolov7网络并使用自己的数据集进行训练，对比实验结果，总结经验。
## 1.Now 

yolov7网络使用yaml文件进行加载，所以修改yaml文件和相关代码可以达到修改网络的目的![]()

```
1.yolov7_ConvSE

2.yolov7_ACmix

3.yolov7_PConv
```
### [yolov7_ConvSE](https://github.com/maple0leaves/YOLOv7_Change/blob/master/cfg/training/yolov7_ConvSE.yaml)
![yolov7_ConvSE](https://github.com/maple0leaves/YOLOv7_Change/blob/master/images/ConvSE.png)
### [yolov7_ACmix](https://github.com/maple0leaves/YOLOv7_Change/blob/master/cfg/training/yolov7ACmix.yaml)
![yolov7_ACmix](https://github.com/maple0leaves/YOLOv7_Change/blob/master/images/ACmix.png)
### [yolov7_PConv](https://github.com/maple0leaves/YOLOv7_Change/blob/master/cfg/training/yolov7_Pconv.yaml)
![yolov7_PConv](https://github.com/maple0leaves/YOLOv7_Change/blob/master/images/PConv.png)
## 2.Results Comparison
|            改进            | Precision | Recall | mAP@0.5 | mAP@0.5:0.95 |
| :------------------------: | :-------: | :----: | :-----: | :----------: |
| yolov7_ConvSE_PConv_origin |   0.883   | 0.916  |  0.939  |    0.527     |
|       yolov7_ConvSE        |   0.746   | 0.749  |  0.761  |    0.373     |
|        yolov7_PConv        |     -     |   -    |    -    |      -       |
|    yolov7_ACmix_origin     |   0.889   | 0.965  |  0.934  |    0.541     |
|        yolov7_ACmix        |   0.906   | 0.968  |  0.941  |    0.556     |

## 3.Attention

yolov7_ConvSE_PConv_origin ,yolov7_ConvSE,yolov7_PConv 在epoch=100下使用[hand_glove(samll)](https://github.com/maple0leaves/YOLOv7_Change/tree/master/ourdata)自定义数据集进行训练,硬件环境RTX3090.

yolov7_ConvSE_PConv_origin 使用[yolov7.yaml](https://github.com/maple0leaves/YOLOv7_Change/blob/master/cfg/training/yolov7.yaml)进行训练

yolov7_ConvSE使用[yolov7_ConvSE.yaml](https://github.com/maple0leaves/YOLOv7_Change/blob/master/cfg/training/yolov7_ConvSE.yaml)进行训练

yolov7_PConv 使用[yolov7_Pconv.yaml](https://github.com/maple0leaves/YOLOv7_Change/blob/master/cfg/training/yolov7_Pconv.yaml)进行训练

yolov7_ACmix_origin,yolov7_ACmix 在epoch=300下使用[electenclasses](https://github.com/maple0leaves/YOLOv7_Change/tree/master/ourdata)自定义数据集进行训练，硬件环境RTX3090

yolov7_ACmix_origin使用[yolov7.yaml](https://github.com/maple0leaves/YOLOv7_Change/blob/master/cfg/training/yolov7.yaml)进行训练

yolov7_ACmix 使用[yolov7ACmix.yaml](https://github.com/maple0leaves/YOLOv7_Change/blob/master/cfg/training/yolov7ACmix.yaml)进行训练

## 4.Conclusion

yolov7_ConvSE各项指标都下降

yolov7_PConv各项指标都下降

yolov7_ACmix各项指标均提升
