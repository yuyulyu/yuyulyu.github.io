---
title: "Datawhale AI 夏令营 - CV：物体检测算法 YOLO"
description: 物体检测算法 YOLO
author: yoyo
date: 2024-08-29 23:53:00 +0800
categories: [Artificial Intelligence, Datawhale]
tags: [CV, YOLO]
mermaid: true
math: true
image:
  path: /assets/covers/datawhale/datawhale-AI-CV-task-1.png
  alt: Datawhale AI CV Task 2 Cover
---


![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/55cd429525804084ab54b7444ec7d36e.png#pic_center)


# 物体检测算法

在计算机视觉中，算法主要分为以下几个种类：

- **图像分类**：识别图像整体属于哪个类别。它不关心图像中的具体物体位置，只关注整个图像的类别。（如AlexNet、VGG、ResNet等）。
- **图像分割**：将图像划分为若干个部分或区域，并为每个像素分配一个标签，从而识别出图像中的不同对象或场景。其中，图像分割具体又可以分类进一步分为<ins>语义分割</ins>和<ins>实例分割</ins>（如U-Net、Mask R-CNN等）。
- **物体检测**：物体检测不仅要识别图像中的对象类别，还要确定它们在图像中的具体位置，以边界框的形式标记出来。（如YOLO、Faster R-CNN和SSD等）。
- **姿态估计**：确定图像或视频中人体的关键点位置，如关节位置，进而重建人体姿态。通常用于行为识别和动作分析（如OpenPose）。
- **场景理解**：结合了分类、分割和检测的任务，试图理解图像中的整体场景布局。不仅关注单个物体，还考虑物体之间的关系和场景的全貌。

## 关键概念和步骤
物体检测算法不仅要识别图像中的对象属于哪个类别，还要确定它们在图像中的具体位置，通常以边界框（bounding box）的形式表示。以下是物体检测的一些关键概念和步骤[^datawhale]：
### 输入
![Urban Object Detection Dataset[^uodd]](https://i-blog.csdnimg.cn/direct/92c2976a702e455eb0a9cbcc54a5edd9.jpeg#pic_center)


物体检测算法的输入通常是一张图像或视频帧，在训练阶段，为了训练一个物体检测模型，数据集通常包含已标注的图像或视频帧。典型的数据集由以下几个文件或部分组成：
- **图像文件**：通常以JPEG、PNG或其他常见的图像格式存储。每张图像可能包含一个或多个对象，且这些对象的类别和位置将用于训练模型。
- **标注文件（Annotations）**：每个文件存储每张图像中物体的位置信息和类别标签，通常以`XML`、`JSON`或`TXT`格式存储。
- **类别文件（Classes）**：用于列出数据集中所有可能的物体类别。
## 特征提取
算法使用深度学习模型（如卷积神经网络CNN）来提取图像的特征。这些特征捕捉了图像中的视觉信息，为后续的物体识别和定位提供基础。一些特征提取算法包括：
- **PCA（主成分分析）**：一种常用的降维技术，通过寻找图像数据的主成分，将数据映射到低维空间，以减少计算复杂度。
- **LDA（线性判别分析）**：另一种降维方法，主要用于分类问题，通过最大化类间方差与类内方差的比率来找到最佳分离超平面。
- **ICA（独立成分分析）**：用于分离信号中的独立成分，特别适用于图像信号处理中信号源的分离。

![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/cc7c8fbe0f014669bb5597c221a7fe32.png#pic_center)

## 候选区域生成
在某些检测算法中，如基于区域的卷积神经网络（R-CNN）及其变体，首先需要生成图像中的候选区域，这些区域可能包含感兴趣的物体。
- **选择性搜索（Selective Search）**：早期R-CNN方法中使用的一种生成候选区域的技术。通过先将图像划分成多个小的分割区域，然后基于颜色、纹理、大小等特征，将相似的区域合并，最终生成不同尺度的候选区域。
- **区域建议网络（Region Proposal Network, RPN）**：RPN是一个轻量级的卷积神经网络，直接在图像上滑动窗口，预测每个位置上的候选区域。这些区域不仅包含潜在的物体，还对其进行粗略的边界框定位。
## 区域分类和边界框回归
对于每个候选区域，算法需要判断它是否包含特定类别的物体，并预测物体的边界框。这通常涉及到分类任务和回归任务的结合。

## 非极大值抑制（NMS）
在检测过程中，可能会产生多个重叠的边界框，用于表示同一物体。NMS是一种常用的技术，用于选择最佳的边界框并去除多余的框。
1. 首先，对所有检测到的边界框按照它们的置信度分数进行排序。
2. 选择得分最高的那个框，并将其作为最终的检测结果之一。
3. 抑制重叠框：对于剩余的框，计算它们与当前选中框之间的重叠度（通常使用IoU 交并比来衡量）。如果某个框与当前框的重叠度超过了一个预设阈值（比如0.5），就将它从候选框中移除。

# One-Stage & Two-Stage 

物体检测算法又分为两类， One-Stage和Two-Stage模型。
![Two stage vs one stage object detection models.[^image]](https://i-blog.csdnimg.cn/direct/673360a39af84700a2990a2c774c58d0.png)
## One-Stage 
One-Stage模型（单阶段模型）指的是在单个卷积神经网络（CNN）中同时进行物体检测中的类别预测和位置回归任务。相比Two-Stage模型，One-Stage模型不需要显式的候选区域生成步骤，而是直接对整张图像进行全局分析，预测图像中所有物体的类别和位置信息。

### 特点

- **优点**：
	- **实时性**：由于处理速度快，One-Stage模型非常适合需要实时处理的场景如视频流的物体检测、自主驾驶等。
	- **实现简单**：模型结构通常较为简单，不需要复杂的区域提议机制。
- **缺点**：
	- **精度较低**：由于模型直接在整张图像上进行检测，可能会错过一些小物体或难以精确定位物体边界。尤其是在处理复杂场景时，精度可能不如Two-Stage模型。

### 代表性模型：
- YOLO（You Only Look Once）
- SSD（Single Shot Detection）

## Two-Stage模型

Two-Stage模型将物体检测任务分解为两个独立的阶段：第一阶段生成候选区域，第二阶段对这些候选区域进行分类和边界框回归。这个分阶段的处理方式使得Two-Stage模型能够在检测精度上具有优势，尽管计算速度可能较慢。

### 特点
- **优点**：
	- **高精度**：分阶段的处理使得Two-Stage模型在复杂场景中能够更准确地识别和定位物体，适合对检测精度要求高的任务。
	- **可扩展性**：通过增加更多的处理阶段，Two-Stage模型可以扩展来处理更复杂的任务，如实例分割、姿态估计等。
- **缺点**：
	- **速度较慢**：由于分成两个独立的阶段处理，Two-Stage模型的计算时间较长，不适合实时应用。
	- **实现复杂**：模型结构和训练过程相对复杂，需要对不同阶段进行单独的调优。

### 代表性模型
- Faster R-CNN
- Mask R-CNN

## 模型的选择

One-Stage模型因为省略了区域提议步骤，所以能够实现更快的检测速度，但这可能会以牺牲一些精度为代价。相比之下，Two-Stage模型通过两步过程提高了检测的准确性，但同时也增加了计算的复杂性和时间消耗  。

在实际应用中，选择哪种模型取决于特定场景的需求。如果对速度有较高要求，如视频流处理或实时监控，One-Stage模型可能更合适。如果对精度有更高要求，如在需要高精度识别的科研或专业领域，Two-Stage模型可能更加适用 。

# YOLO算法

YOLO，全称为"You Only Look Once"，是One-Stage模型的一种。YOLO的核心思想是将目标检测任务视为一个单一的回归问题，直接从图像像素到边界框坐标和类别概率的映射。这种设计使得YOLO能够以非常快的速度进行目标检测，同时保持较高的精度，适合需要实时处理的应用场景。[^datawhale]

![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/dedc0c8f8846456ba0120eaedfc16450.png#pic_center)
 ## 数据集格式
其中，YOLO支持多种数据集格式[^yolodataset]，比如YOLO数据集格式则是最常见的一种。除此之外 [JSON2YOLO](https://github.com/ultralytics/JSON2YOLO)也支持将现有数据集从其他格式转换为YOLO数据集。

YOLO数据集格式主要使用`.txt`文件来存储图像中物体的标注信息。每个图像都有一个对应的`.txt`文件，文件中的每行表示一个物体的标注，包括物体的类别索引和边界框（bounding box）的坐标。
1. **类别索引**：每个物体的类别由一个整数索引表示，索引对应于预先定义的类别列表。
2. **边界框坐标**：边界框由其中心点坐标`(x_center, y_center)`和宽度`width`、高度`height`组成。这些值通常是归一化到图像宽度和高度的比例值，范围在`0`到`1`之间。
3. **坐标格式**：边界框坐标通常按照`[class_index x_center y_center width height]`的格式记录，其中:
	- `class_index`是类别索引。
	- `x_center` 和 `y_center` 是边界框中心点的`x`和`y`坐标。
	- `width` 和 `height` 是边界框的宽度和高度。
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/3115a10e5f354c4b8f73863791e9b943.png#pic_center)

在YOLO的训练过程中，这样的配置文件允许用户轻松地指定数据集的位置和类别信息，从而无需硬编码在训练脚本中。

```python
# Train/val/test sets as 1) dir: path/to/imgs, 2) file: path/to/imgs.txt, or 3) list: [path/to/imgs1, path/to/imgs2, ..]
path: ../dataset/  # 指定了数据集相对于当前配置文件的路径或者相对于执行训练脚本的根目录路径
train: images/train/  # 定义了训练集图像的相对路径
val: images/val/  # 定义了验证集图像的相对路径

# Classes
nc: 2  # 表示类别的数量，这里设置为2，意味着数据集中有两类物体需要被识别
names: ["0", '1']  # 一个列表，包含了每个类别的名称。这里有两个类别，名称分别是"0"和"1"。
```

赛题对应使用示例：

```python
with open('yolo-dataset/yolo.yaml', 'w', encoding='utf-8') as up:
    up.write(f'''
path: {dir_path}/yolo-dataset/
train: train/
val: val/

names:
    0: 非机动车违停
    1: 机动车违停
    2: 垃圾桶满溢
    3: 违法经营
''')
```
## 训练日志
在使用YOLO进行训练时，生成的`exp/detect/train`类型的文件夹是训练过程中的一个关键组成部分。

- **模型权重** (`.pt `或` .pth `文件): 训练过程中保存的模型权重，可以用于后续的测试或继续训练。
- **日志文件** (`.log` 文件): 包含训练过程中的所有输出信息，如损失值、精度、速度等。
- **配置文件** (`.yaml `或` .cfg` 文件): 训练时使用的配置文件副本，记录了数据路径、类别名、模型架构等设置。
- **图表和可视化**: 有时YOLO会生成训练过程中的性能图表，如损失曲线、精度曲线等。
- **测试结果**: 如果训练过程中包括了测试阶段，可能会有测试结果的保存，如检测结果的图片或统计数据。

在训练过程中和训练完成后，都可以查看训练日志。可以优先查看results.png。从验证集上的损失 (`val/box_loss`, `val/cls_loss`, `val/dfl_loss`) 和性能指标可以评估模型在未见数据上的泛化能力。
# 参考
[^datawhale]: Datawhale - Task2：建模方案解读与进阶[https://datawhaler.feishu.cn/wiki/LiZswOp27ieilak4suRcYI9Knlf#XiMVdKRU9oNqFpxaQbvcxp31nGf](https://datawhaler.feishu.cn/wiki/LiZswOp27ieilak4suRcYI9Knlf#XiMVdKRU9oNqFpxaQbvcxp31nGf)
[^image]:Semantic Image Cropping - Scientific Figure on ResearchGate. Available from: [https://www.researchgate.net/figure/Two-stage-vs-one-stage-object-detection-models_fig3_353284602](https://www.researchgate.net/figure/Two-stage-vs-one-stage-object-detection-models_fig3_353284602)
[^yolodatasetformat]:[YOLOv8] - YOLO数据集格式介绍和案例：[https://blog.csdn.net/u011775793/article/details/134918087](https://blog.csdn.net/u011775793/article/details/134918087)
[^yolodataset]:Ultralytics-dataset-format: [https://docs.ultralytics.com/tasks/detect/#dataset-format](https://docs.ultralytics.com/tasks/detect/#dataset-format)
[^uodd]: Urban Object Detection Dataset: [https://www.v7labs.com/open-datasets/urban-object-detection-dataset](https://www.v7labs.com/open-datasets/urban-object-detection-dataset)
