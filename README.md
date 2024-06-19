# 智慧餐饮结算系统(整理的大一年度项目)
## 简单且便宜的实现方案

该项目致力于实现一个极其简单且成本低廉的智慧餐饮结算系统，总耗资仅需400元（使用OpenMV开发板，实际上可以用其他开发板和摄像头模块以降低成本）。

## 项目简介（服务器端和摄像头端的代码找不着了）

本项目利用图像处理和机器学习技术，对餐饮图片进行识别与结算。为了实现这一目标，我们采用了以下方案：

1. **数据集**：
    - 使用ChineseFoodNet数据集，该数据集包含18万张图片，涵盖208类食物。遗憾的是，数据集中都是单个食物的照片，意味着在实际应用中，我们需要自动分割出照片中的多款菜品，并分别进行识别。（可以在百度的飞桨平台训练，每天白嫖一点算力卡用它的大显存的显卡训练）

2. **图片处理与分割**：
    - 我们先对图片进行二值化处理，去除小洞和杂乱的点。
    - 然后设定一个范围，使用霍夫变换识别椭圆，找到圆心和长短轴。
    - 最后，将识别出的各个菜品裁剪出来，分别进行识别。

## 详细实现

### 1. 图片处理

#### 二值化处理
对图片进行二值化，将图像转换为黑白图像，以便后续处理。

#### 去除杂点
使用图像处理算法去除图像中的小洞和杂乱的点，以提高识别的准确性。

### 2. 分割与识别

#### 霍夫变换识别椭圆
通过霍夫变换算法，识别出图像中的椭圆，找到各个菜品的位置。

#### 裁剪与识别
根据识别出的椭圆位置，裁剪出各个菜品，并分别进行识别。

### 3. 结算流程

#### 双摄像头设计
- **正面摄像头**：用于结算，顾客出示二维码，系统自动扣款。
- **背面摄像头**：用于采集和识别菜品。

### 系统架构

1. **OpenMV1**：
    - 负责图像处理与识别，低成本且高效。
2. **OpenMV2**：
    - 用于采集菜品图像。
3. **二维码识别模块**：
    - 用于结算。

## 视频演示
项目的视频演示可以参考以下链接：

