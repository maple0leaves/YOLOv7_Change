# YOLOv7_Change
修改yolov7网络并使用自己的数据集进行训练，对比实验结果，总结经验。

实验后的结果都保存在[result](https://github.com/maple0leaves/YOLOv7_Change/tree/master/results)

## 1.Now 

```
目前改进:
1.yolov7_ConvSE

2.yolov7_ACmix

3.yolov7_PConv
```

yolov7网络使用yaml文件进行加载，所以修改yaml文件和相关代码就可以达到修改网络的目的![change_yaml](https://github.com/maple0leaves/YOLOv7_Change/blob/master/images/change_yaml.png)

### [yolov7_ConvSE](https://github.com/maple0leaves/YOLOv7_Change/blob/master/cfg/training/yolov7_ConvSE.yaml)
![yolov7_ConvSE](https://github.com/maple0leaves/YOLOv7_Change/blob/master/images/ConvSE.png)
### [yolov7_ACmix](https://github.com/maple0leaves/YOLOv7_Change/blob/master/cfg/training/yolov7ACmix.yaml)
![yolov7_ACmix](https://github.com/maple0leaves/YOLOv7_Change/blob/master/images/ACmix.png)
### [yolov7_PConv](https://github.com/maple0leaves/YOLOv7_Change/blob/master/cfg/training/yolov7_Pconv.yaml)
![yolov7_PConv](https://github.com/maple0leaves/YOLOv7_Change/blob/master/images/PConv.png)
## 2.Results 
|        改进名称         | Precision | Recall | mAP@0.5 | mAP@0.5:0.95 |
| :---------------------: | :-------: | :----: | :-----: | :----------: |
|    yolov7_origin_100    |   0.883   | 0.916  |  0.939  |    0.527     |
|    yolov7_origin_300    |   0.872   | 0.929  |  0.946  |    0.542     |
|    yolov7_ConvSE_100    |   0.746   | 0.749  |  0.761  |    0.373     |
|    yolov7_ConvSE_300    |   0.886   | 0.947  |  0.959  |    0.565     |
|    yolov7_PConv_100     |   0.838   | 0.879  |  0.894  |    0.468     |
| yolov7_ACmix_origin_300 |   0.889   | 0.965  |  0.934  |    0.541     |
|    yolov7_ACmix_300     |   0.906   | 0.968  |  0.941  |    0.556     |

## 3.Attention

所有比较指标都是使用最后一轮的结果，改进名称最后的数字表示训练epoch的次数

yolov7_origin_100,yolov7_origin_300,yolov7_ConvSE_100,yolov7_ConvSE_300,yolov7_PConv_100使用[hand_glove(samll)](https://github.com/maple0leaves/YOLOv7_Change/tree/master/ourdata)自定义数据集进行训练,硬件环境RTX3090.

yolov7_origin 使用[yolov7.yaml](https://github.com/maple0leaves/YOLOv7_Change/blob/master/cfg/training/yolov7.yaml)进行训练

yolov7_ConvSE使用[yolov7_ConvSE.yaml](https://github.com/maple0leaves/YOLOv7_Change/blob/master/cfg/training/yolov7_ConvSE.yaml)进行训练

yolov7_PConv 使用[yolov7_Pconv.yaml](https://github.com/maple0leaves/YOLOv7_Change/blob/master/cfg/training/yolov7_Pconv.yaml)进行训练

yolov7_ACmix_origin_300,yolov7_ACmix_300 使用[electenclasses](https://github.com/maple0leaves/YOLOv7_Change/tree/master/ourdata)自定义数据集进行训练，硬件环境RTX3090

yolov7_ACmix_origin使用[yolov7.yaml](https://github.com/maple0leaves/YOLOv7_Change/blob/master/cfg/training/yolov7.yaml)进行训练

yolov7_ACmix 使用[yolov7ACmix.yaml](https://github.com/maple0leaves/YOLOv7_Change/blob/master/cfg/training/yolov7ACmix.yaml)进行训练

## 4.Conclusion

yolov7_ConvSE_100相对于yolov7_origin_100，各项指标虽然都下降,但是最后yolov7_ConvSE_100各项指标的**上升趋势更大**，我认为是训练次数不够的原因。

yolov7_ConvSE_300相对于yolov7_origin_300各项指标**均提升**，可以作为改进网络的思路。

yolov7_PConv_100各项指标都**下降**,但是网络的**参数减少** ，需要权衡使用。

yolov7_ACmix_300各项指标**均提升**，可以作为改进网络的思路。

**注**:各项指标指的是Results中比较的指标
