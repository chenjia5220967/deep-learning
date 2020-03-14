### 常用深度学习框架

#### 2019.10.16

深度学习研究的热潮持续高涨，各种开源深度学习框架也层出不穷，其中包括TensorFlow、Caffe、Keras、CNTK、Torch7、MXNet、Leaf、Theano、DeepLearning4、Lasagne、Neon等。我们参考开源的测试结果，结合自己整理的数据，针对主流的深度学习框架进行简单对比及介绍。

| 框架 | 机构 | 支持语言 | Stars | Forks |
| --------------------------------------------------------- | ----------- | ------------------- | ---------- | ----- |
| [Caffe](https://github.com/BVLC/caffe)                    | BVLC        | C++/Python/Matlab   |    ![](https://img.shields.io/github/stars/BVLC/caffe.svg)   | ![](https://img.shields.io/github/forks/BVLC/caffe.svg) |
| [CNTK](https://github.com/Microsoft/CNTK)                 | Microsoft   | C++                 |    ![](https://img.shields.io/github/stars/Microsoft/CNTK.svg)   | ![](https://img.shields.io/github/forks/Microsoft/CNTK.svg) |
| [Keras](https://github.com/keras-team/keras)                     | François Chollet    | Python              |    ![](https://img.shields.io/github/stars/keras-team/Keras.svg)   | ![](https://img.shields.io/github/forks/keras-team/Keras.svg) |
| [Tensorflow](https://github.com/tensorflow/tensorflow)    | Google      | Python/C++/Go...    |    ![](https://img.shields.io/github/stars/tensorflow/Tensorflow.svg)   | ![](https://img.shields.io/github/forks/tensorflow/Tensorflow.svg) |
| [MXNet](https://github.com/apache/incubator-mxnet)        | DMLC        | Python/C++/R...     |    ![](https://img.shields.io/github/stars/apache/incubator-mxnet.svg)   | ![](https://img.shields.io/github/forks/apache/incubator-mxnet.svg) |
| [PyTorch](https://github.com/pytorch/pytorch)             | Facebook    | Python              |    ![](https://img.shields.io/github/stars/pytorch/pytorch.svg)   | ![](https://img.shields.io/github/forks/pytorch/pytorch.svg) |



###  性能对比


#### 1. 训练时间: Network DenseNet-121 (Multi-GPU)

**运行于 SSD 硬盘**

| 框架    | 1xV100/CUDA 9/CuDNN 7 | 4xV100/CUDA 9/CuDNN 7 |
| --------------- | :------------------:  | :------------------:  |
| Pytorch         | 27min                 | 10min                 |
| Keras(TF)       | 38min                 | 18min                 |
| Tensorflow      | 33min                 | 22min                 |
| MXNet(Gluon)    | 29min                 | 10min                 |

**运行于RAM内存中**

| 框架    | 1xV100/CUDA 9/CuDNN 7 | 4xV100/CUDA 9/CuDNN 7 |
| -------------- | :------------------:  | :------------------:  |
| Pytorch        | 25min                 | 8min                  |
| Keras(TF)      | 36min                 | 15min                 |
| Tensorflow     | 25min                 | 14min                 |
| MXNet(Gluon)   | 28min                 | 8min                  |



#### 2. 1000张图片推理时间(s): Network ResNet-50

| 框架      | K80/CUDA 8/CuDNN 6 | P100/CUDA 8/CuDNN 6 |
| ---------------- | :----------------: | :-----------------: |
| CNTK             | 8.5                | 1.6                 |
| Keras(TF)        | 10.2               | 2.9                 |
| Tensorflow       | 6.5                | 1.8                 |
| MXNet            | 7.7                | 1.6                 |
| PyTorch          | 7.7                | 1.9                 |


#### 3. CPU推理时间(s): E5-2630v4, Network FCN5

|    框架     |   1 Thread | 2 Threads | 4 Threads | 8 Threads | 16 Threads | 32 Threads |
| ----------- | :--------: | :-------: |  :-----: | :-----: | :-----: | :------: |
| Caffe       | 1887.2ms   | 1316.7ms  | 1051.8ms | 952.1ms | 952.3ms | 834.7ms  |
| CNTK        | 1238.7ms   | 616.3ms   | 352.7ms  | 229.5ms | 155.9ms | 192.4ms  |
| Tensorflow  | 992.2ms    | 773.6ms   | 419.3ms  | 252.3ms | 149.7ms | 124.7ms  |
| MXNet       | 1386.8ms   | 915.5ms   | 559.0ms  | 499.1ms | 416.3ms | 413.9ms  |


### 框架评价

| 框架  |安装成本| 代码理解程度 | API丰富程度 | 模型丰富程度 | 文档完整程度 |训练与测过程 | 学习资源
| ------------------ | :----: | :----: | :----: | :----: | :----: | :----: | :----: |
| CNTK               | 良好   | 良好    | 良好   | 良好    | 优秀   | 良好   | 良好  |
| Keras              | 良好   | 良好    | 优秀   | 优秀    | 良好   | 优秀   | 良好  |
| MXNet              | 良好   | 良好    | 良好   | 良好    | 良好   | 优秀   | 优秀  |
| Pytorch            | 优秀   | 优秀    | 良好   | 良好    | 优秀   | 良好   | 良好  |
| Tensorflow         | 良好   | 良好    | 优秀   | 优秀    | 优秀   | 优秀   | 优秀  |
| Caffe              | 良好   | 优秀    | 良好   | 良好    | 优秀   | 良好   | 优秀  |



### 推荐框架


目前众多的深度学习框架，使用者只要选择适合自己的框架即可，我们在日常使用中，考虑到训练的快捷程度，部署难度以及对CNN、RNN模型的直接程度，推荐以下几款深度学习框架。


#### 1.Keras

Keras 提供了简单易用的 API 接口，入门快，特别适合初学者入门。其后端采用 TensorFlow, CNTK，以及 Theano。另外，Deeplearning4j 的 Python 也是基于 Keras 实现的。Keras 几乎已经成了 Python 神经网络的接口标准。

#### 2.TensorFlow

谷歌出品，追随者众多。代码质量高，支持模型丰富，支持语言多样， TensorBoard 可视化工具使用方便。

#### 3.MXNet

已被亚马逊选为 AWS 上的深度学习框架，支持动态图计算。MXNet 有许多中国开发者，因而有非常良好的中文文档支持。Gluon 接口使得 MXNet 像 Keras 一样简单易用。


### 参考资料
1. [香港浸会大学深度学习框架Benchmark](http://dlbench.comp.hkbu.edu.hk/?v=v8)
2. [DeepLearningFrameworks](https://github.com/ilkarman/DeepLearningFrameworks)
3. [博客](http://app.myzaker.com/news/article.php?pk=5a13b55c1bc8e05d71000016)
4. [开发者如何选择深度学习框架?](https://www.zhihu.com/question/68114194/answer/465874315)
