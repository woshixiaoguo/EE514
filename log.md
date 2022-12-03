# EE514
Assignment 分为两个部分。
第一部分从人体穿戴传感器中预测人类行为，主要关注 data wrangling 和经典统计机器学习技术的应用
第二部分侧重于另一个问题：检测火星图像中是否存在某些特征，学生将被要求使用基于深度学习的方法，如卷积神经网络。

## 提交材料
最后提交的材料应该是一份报告，记录所有假设、设计决定和结果。包括可视化、情节和表格。您应该努力仅使用报告文档使您的作品完全可重现：包括您测试的所有内容和所有结果的详细信息。
记录所有设计决策并说明其合理性。
还要为每个部分提交带有最佳模型的 notebook。

不能提交代码图片，要提交代码文本


## 任务一：Extrasensory

### 提升测试集
选择五个不同的用户，并在每个用户上单独测试模型。评估五个用户测试指标的平均值和方差（例如准确性）。将用户组合成一个测试集，以减少测试指标的差异。

### 验证数据
提供的入门代码中没有模型选择。相反，代码只是对一个用户的数据进行训练，然后在另一个用户上进行测试。引入一个由多个用户组合的验证集。

### 训练数据增加
通过评估适当的数据拆分的结果，调查当您更改用于培训的用户时会发生什么。将多个用户组合成一个更大的培训集，并在适当的数据拆分上评估结果。

### 模型选择
逻辑回归的C参数调节了应用于模型的正则化的强度。调查当这种情况增加或减少时会发生什么。从scikit-learn软件包中尝试额外的机器学习算法，并比较结果。还要调整这些模型的超参数。

### 模型测试
在保留的测试集上评估所选模型。估计OOS误差，并评估sklearn.metrics包中的各种其他指标，例如平衡精度、精度、召回、F1和ROC-AUC。分析和解释结果的含义，并评论您认为您创建的模型在现实世界中效果如何。绘制ROC曲线并对其进行评论。

### 预测其他行为
扩展之前的工作，以预测散步以外的其他行为，例如坐着或骑自行车。根据需要介绍其他功能。

## 任务二：Planet Four
在任务的这一部分，您将尝试使用深卷积神经网络从图像中识别火星表面是否存在特征。有两个有趣的特征：风扇和斑点。您将使用的数据集是行星四号公民科学项目中注释的数据的低分辨率版本。

### 训练模型
使用提供的入门代码来训练5个纪元的ResNet50模型（通过数据集）。您可以在自己的机器上或使用Google Colab或Gradient执行此操作。如果您使用的是这些平台之一，则需要上传笔记本和数据。

注意每个时代之后，训练例程将报告验证损失和准确性。尝试为更多时代进行训练（注意：再次调用train（）将更长时间地训练当前模型，而不是从头开始训练新模型）。绘制学习曲线，并评论报告中实现的准确性。修改训练例程，在每个纪元后保存模型的检查点。

### 实验
尝试使用torchvision.models的不同网络架构进行训练，看看您是否可以提高验证准确性。尝试不同的学习率和不同的优化器，如来自torch.optim的Adam。尝试来自torchvision.transforms的不同数据增强策略。

### 验证
更新notebook，以评估测试集上最终选择的模型。