title: Datawhale AI 夏令营 
description: 2024 大运河杯数据开发应用创新大赛 - 城市治理赛道
author: yoyo
date: 2024-08-26 14:31:00 +0800
categories: [AI]
tags: [CV]
mermaid: true
---

## 赛题解读

![Desktop View](/assets/image/AI/Datawhale/dayunhebei.jpeg)

### 赛题目标

随着城市化进程的加快，城市管理面临着前所未有的挑战。占道经营、垃圾堆放和无照经营游商等问题对城市管理提出了更高的要求。本赛道聚焦城市违规行为的智能检测，要求选手研究开发高效可靠的计算机视觉算法，提升违规行为检测识别的准确度，降低对大量人工的依赖，提升检测效果和效率，从而推动城市治理向更高效、更智能、更文明的方向发展，为居民创造一个安全、和谐、可持续的居住环境。

### 赛事资源分析

初赛提供城管视频监控数据与对应违规行为标注。违规行为包括垃圾桶满溢、机动车违停、非机动车违停等。视频数据为mp4格式，标注文件为json格式，每个视频对应一个json文件。

- frame_id：违规行为出现的帧编号
- event_id：违规行为ID
- category：违规行为类别
- bbox：检测到的违规行为矩形框的坐标，[xmin,ymin,xmax,ymax]形式

标注示例

```json
[
  {
   "frame_id": 20,
   "event_id": 1,
   "category": "机动车违停",
   "bbox": [200, 300, 280, 400]
  },
  {
   "frame_id": 20,
   "event_id": 2,
   "category": "机动车违停",
   "bbox": [600, 500, 720, 560]
  },
  {
   "frame_id": 30,
   "event_id": 3,
   "category": "垃圾桶满溢",
   "bbox": [400, 500, 600, 660]
  }
 ]
```

### 违法评判标准

| **机动车违停** | **非机动车违停** | **垃圾满溢** |
|---------------------|---------------------------|----------------------------------|
| 机动车在设有禁止停车标志、<br>标线的路段停车，或在非机<br>动车道、人行横道、施工地<br>段等禁止停车的地方停车。|  非机动车（如自行车、‌电动<br>车等）‌未按照规定停放在指<br>定的非机动车停车泊位或停<br>车线内，‌而是在非机动车禁<br>停区域或未划定的区域<br>（消防通道、盲道、非机动<br>车停车区线外、机动车停车<br>区等）随意停放。  |   生活垃圾收集容器内垃圾超过<br>三分之二以上即为满溢。‌垃<br>圾桶无法封闭、脏污且周边<br>有纸屑、污渍、塑料、生活<br>垃圾及杂物堆放。|
|![Desktop View](/assets/image/AI/Datawhale/jidongcheweiting.png) | ![Desktop View](/assets/image/AI/Datawhale/feijidongcheweiting.png) | ![Desktop View](/assets/image/AI/Datawhale/jidongcheweiting.png) | lajitongmanyi.png |

### 评分规则介绍

使用F1score、MOTA指标来评估模型预测结果。

![Desktop View](/assets/image/AI/Datawhale/F1score.png)

对每个json文件得到两个指标的加权求和，最终得分为所有文件得分取均值。[^1][^2]

[^1]:注1：若真实目标框与预测框IOU大于0.5，则判定目标正确识别。若MOTA指标为负，则该类别精度得分为0。
[^2]:注2：若该视频中没有某个类别的目标，则此类别计算均值时，忽略该视频。

### 任务提交格式

初赛任务是根据给定的城管视频监控数据集，进行城市违规行为的检测。违规行为主要包括垃圾桶满溢、机动车违停、非机动车违停等。选手需要能够从视频中分析并标记出违规行为，提供违规行为发生的时间和位置信息。

## 目标检测系统 - YOLO

![Desktop View](/assets/image/AI/Datawhale/yolo-timeline.png)

You Only Look Once（YOLO），是一种流行的实时目标检测系统，由Joseph Redmon等人在2015年提出。YOLO模型的核心思想是将目标检测任务视为一个单一的回归问题，通过一个卷积神经网络（CNN）直接从图像像素到边界框坐标和类别概率的映射。YOLO模型经过了多次迭代，包括YOLOv2（YOLO9000）、YOLOv3和YOLOv4等版本，每个版本都在性能和速度上有所提升，同时也引入了一些新的技术，如更深的网络结构、更好的锚框机制、多尺度特征融合等。

![Desktop View](/assets/image/AI/Datawhale/yolo-example.png)

**YOLO的特点**

1. **端到端训练**：YOLO 将目标检测任务视为单一的回归问题，可以在一次前向传播中同时预测多个目标的类别和边界框坐标，避免了其他目标检测算法中冗长的候选框生成和分类过程。
2. **高效的实时性**：由于 YOLO 的网络结构设计和直接回归方法，YOLO 在运行速度上非常快，特别适用于实时场景下的目标检测任务。
3. **全局推理**：YOLO 对整幅图像进行检测，而不像其他方法仅在局部区域进行预测。这使得 YOLO 对复杂背景和不规则物体具有较好的鲁棒性。

### 标注格式

![Desktop View](/assets/image/AI/Datawhale/yolo-labeling-structure.png){: .left }

YOLO使用的标注格式是每张图像一个文本文件，文件名与图像文件名相对应。

```csharp
<class> <x_center> <y_center> <width> <height>`。
```

- `<class>`：类别的索引号。
- `<x_center>`：边界框中心点的 x 坐标，相对于图像宽度的归一化比例。
- `<y_center>`：边界框中心点的 y 坐标，相对于图像高度的归一化比例。
- `<width>`：边界框的宽度，相对于图像宽度的归一化比例。
- `<height>`：边界框的高度，相对于图像高度的归一化比例。

**YOLO标注格式的转换**

YOLO 的标注文件只需要记录归一化的坐标，适用于不同大小的图像。

```python
x_min, y_min, x_max, y_max = bbox
    x_center = (x_min + x_max) / 2 / img_width
    y_center = (y_min + y_max) / 2 / img_height
    width = (x_max - x_min) / img_width
    height = (y_max - y_min) / img_height
```

### 模型训练

```python
from ultralytics import YOLO

# 设置模型版本
model = YOLO("yolov8n.pt") 

# 设定数据集和训练参数
results = model.train(data="yolo-dataset/yolo.yaml", epochs=2, imgsz=1080, batch=16)
```

### 训练日志

每一个epoch会返回3个损失函数：
- `box_loss` 是边界框回归损失，用于评估预测的边界框与真实边界框之间的差异。
- `cls_loss` 是分类损失，用于评估类别预测的准确性。
- `dfl_loss` 是防御性损失，用于提高模型的泛化能力。





