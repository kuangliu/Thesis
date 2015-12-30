# Chapter 1. 绪论

## 引言

表情是人类内心世界最自然的表达方式之一，它在我们的社会交往中扮演着举足轻重的作用。拥有了它，我们可以畅快的表达自己的情感，还可以探究他人的态度和意图。人类可以一眼就能辨别出他人的面部表情，但对于机器来说这是一件非常困难的事情。面部表情自动识别 (Automatic Facial Expression Recognition) 系统能让机器能够读懂并理解人类的情感和意图，对于人机交互 (Human Computer Interaction，缩写HCI) 、实时监控以及社交网络等领域都有着非常重要的促进作用。



## 项目背景与研究意义

### 情感计算与人工智能

随着人工智能的发展，人们对于计算机在情感智能方面的需求也越来越高。计算机将不应是冰冷冷的机器，它应该能与人有感性的交流，能够通过满足人们情感上需求让用户对其逐步建立信任和依赖感。人工智能除了重视机器超越人类的计算能力与感知能力外，也要求其具备与人进行感情交流的能力。它应该是理性与感性交叉发展的结果。强调感性上的人机交互和情感计算已经成为人工智能的一个重要的发展方向。

以近期热卖的由日本软银推出的情感陪护机器人Pepper为例，它能够通过传感器对人类的面部表情和语音语调进行分析，进而达到读懂人类的情感的目的。可见实现情感计算的第一步也是最重要的一步就是赋予机器识别理解情感信号（面部表情、语言、语音语调等）的能力。机器通过对这些信号的分析就能判断出对应的情感，从而做到了理解人类的情感；进而机器还可以通过同一套情感信号来传递自己的情感，这样机器就具有了与人类进行情感交互的能力。

近十几年来，深度学习的发展大大推动了人工智能的进程。复杂的神经网络模型能够在海量高纬度数据中学习出复杂的模式，在包括语音识别、图像识别、自然语言理解等领域取得了令人瞩目的成绩。深度学习模型同样适用且擅长于复杂的情感计算问题。



### 自动表情识别

美国心理学家艾伯特·梅拉比安把人的感情表达效果总结了一个公式：感情的表达＝7%的语言＋38%声音＋55%表情，可见表情在人类所有的感情的外在表达中占据的重要位置。而表情信息通过视觉的方式向外界表达。实现情感计算就要求机器能够对这些流露出的面部表情信息进行收集、分析和识别。自动面部表情识别 (Automated Facial Expression Recognition) 系统能够赋予计算机这样的能力。

早在1972年，美国心理学家Paul Ekman就提出了脸部情感的表达方法以及脸部运动编码系统FACS。通过不同编码和运动单元的组合，表达脸部复杂的表情变化，譬如高兴、恶心、惊讶等。该成果被应用于人脸表情的自动识别与合成上。

近十年来，面部表情识别 (Facial Expression Recognition, 缩写FER) 已经成为情感计算、计算机视觉以及人机交互领域的一个非常热门的研究方向。一个完整的FER系统通常包含三个阶段：1）人脸检测与定位； 2）面部表情特征提取；3）训练一个分类器 (如SVM) 用于分类提取到的特征。其中人脸检测与定位现已成一个独立的研究方向，在本文中都不做描述。



## 研究现状

我们自动表情识别方法分成两类：基于手工特征分类的方法和基于深度学习的方法。基于手工特征分类的方法主要包括选取不同的特征搭配不同的分类算法。而基于深度学习的方法主要包括搭建不同的网络模型。

### 基于手工特征分类的方法

基于特征的识别方法，选择合适的特征尤为关键。要求选取的特征能够代表表情的本质，以便在分类阶段能够很好的把各种表情区分开来。值得注意的是，许多用于人脸识别的特征和方法都可以用于表情识别当中。

基于降维的特征提取算法，如主成分分析(principal component analysis, 缩写PCA)，线性判别分析 (linear discriminate analysis, 缩写LDA)，独立成分分析 (independent component analysis, 缩写ICA) 等，在人脸识别领域已经成为经典方法。这些方法同样可以用于表情识别。[5]提出了一种基于PCA的表情识别方法，并揭示用于识别表情的“主分”和用于识别人脸的“主成”有着重大的差异。[13]将小波变换包含在基于LDA的表情识别方法中，并显示在准确度和时间复杂度上均有所提升。

局部二值模型 (local binary pattern, LBP) 在人脸识别、图像分类等领域都有着广泛的应用，是一种非常优秀的局部特征。它通过对局部区域计算LBP直方图，并将其连接起来做为最终的识别特征。[16, 15]把LBP运用在FER问题上，并取得了不错的效果。

Gabor小波被广泛应用于面脸表情的特征提取。[1]尝试使用一组多尺度、多方向的Gabor滤波器，用于编码面部表情。[11]提出一种基于不同Gabor特征组合的面部表情识别方法。[3]比较了基于SVM分类的ICA与Gabor特征的效果差距。

从上面的描述可见，传统的FER方法都不能逃脱手工特征 (如HOG, LBP, Gabor等) 加分类的框架，当然这也是机器学习的经典框架。这些方法效果有好有坏，但最主要的问题在于其针对某种数据库挑选的特征和训练的参数的泛化能力不强。在现实中因为存在光照、姿势、变形、遮挡等复杂情形，系统输入的测试样本跟训练样本可能存在巨大的差异，这就导致了最终的结果不能让人满意。

### 基于深度学习的方法

卷积网络是近几年用于图像检测、识别和分类领域的一种非常有用的模型。拥有上千万甚至上亿参数的卷积网络能够去拟合大量的、复杂的训练样本，并且卷积网络可以自动从数据中学习出有用的”特征“用于分类，所以卷积网络可以被视成一个有效的自动特征提取器。卷积网络在诸多模式识别问题上应用广泛，包括人脸检测[9]和识别[19]，姿势估计[20]，分类[10,17,18]，视频跟踪[22]。

基于卷积网络模型的方法主要区别在于网络结构设计方面。[14]使用一个包含两个卷积层的卷积网络来尝试解决FER问题；[4]使用了一个更深的，总共包含12层其中有5个卷积层的卷积网络；[7]使用卷积网络来检测微笑，并得到大幅提升准确度的结果。

## 本文组织结构

本文剩余章节的组织结构如下：

第二章介绍人工神经网络模型及其训练方法，包括感知机模型、梯度下降算法、反向传播算法以及各种参数更新方法。除此之外还介绍了过拟合问题和各种正则化的方法。

第三章介绍卷积网络模型，包括卷积网络各层的结构、两种最常用的损失函数，以及一些数据预处理方法。

第四章介绍我们解决FER问题提出的模型，包括各个子网络模型的结构以及整个网络模型的构建方法，还包含一些实现上的细节。

第五章介绍训练时的一些细节，包括数据库的选取、参数的调节等。

第六章对训练的结果进行分析和总结，并对未来工作提供方向和指导。

