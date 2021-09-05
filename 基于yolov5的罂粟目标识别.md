# 基于yolov5的罂粟目标识别

## 文件概述

#### 运行在CUDA10.1 yolov5 python3 下

#### 文件夹名称 yolov5-master

#### 预处理结束的图片 yolov5-master\data_img

#### 图片文件以及labelimg的标注txt文件 yolov5_master\imagetxt

#### 训练的权重文件 yolov5-master\runs\train\best.pt

#### 测试数据 yolov5-master\runs\detect

#### 训练使用的.py文件 train.py

#### 识别使用的.py文件 detect.py

#### 测试使用的.py文件 test.py

具体的函数使用请查看代码注释

权重文件在runs文件的train中 直接使用即可

## 具体操作

### 1、数据收集阶段

首先用python爬虫爬取罂粟的照片

爬虫文件名 py_pachong.py

将其存放到pyyingsu文件夹内

### 2、数据的预处理

对爬取的数据进行预处理，更改图片的尺寸以及文件名

预处理的文件image.py

将图片切分成若干小图

xmlname.py和xmltxt.py负责处理xml文件

### 3、图片标注(labelimg)

使用labelimg 进行图片的标注

标注文件存储为xml形式

通过xmltxt.py文件将xml文件转换成用于训练的txt文件

### 4、模型训练

模型训练前需要更改models和data中的yaml文件里的路径，

更改完成后即可开始训练

结束上述操作后进行模型训练

main方法内更改训练数据：

--weights 修改权重文件(重新训练用空字符 可以接着上次训练)

--cfg和--data 都为模型的yaml文件 分别在models文件夹里和data文件夹里

--epochs为训练次数

### 5、模型测试

完成训练后可使用test.py文件进行测试

### 6、模型使用

使用detect.py进行图像的识别

权重文件使用训练好的best.pt

## 模型优化

### kmeans计算锚框