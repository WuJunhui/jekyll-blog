---
published: true
---
## 前言

楼主近期换了一个环境炼丹，发现有新的分类任务时，这里的人习惯先用 Inception-V3 跑个 baseline 。而我之前总是习惯于用 ResNet-50 跑个 baseline 的。为什么会存在这样的差异呢？

## Inception 和 ResNet 系列在图像分类任务上的对比

我对比了 Inception 系列 和 ResNet 系列论文里列出来的在 ImageNet 上的指标，感觉难以从指标上去衡量，毕竟模型的复杂度、图片分辨率、调参方式、评测时的crop方式等不太一致。根据周边小伙伴自己评测，ResNet-101 > Inception-V3 > ResNet-50，基本上符合“越大的复杂度准确率越高”这个规律。当然后续有将 Inception 和 ResNet 结构结合起来的网络，当然能力更强了，略去不表。

### 一点对论文的吐槽

别的且不说，就看 Inception-V3 的论文中为了刷高指标是怎么评估的：4个 Models, 144个 Crops 的 ensemble[1], 显得有点浮夸。相对来看 ResNet 的论文清爽很多。


## 在其他视觉任务上的表现

根据我的一点不成熟的观察，在检测、分割等其他视觉任务上，大家比较倾向于用 ResNet 系列做 backbone 来跑 baseline. Google Research 自己出的一篇文章[2]对不同的 backbone 和检测框架作对比，在相同的Inference Time 的情况下， ResNet-101 基本上优于 Inception-v3。

![AccuracyVsTime.png]({{site.baseurl}}/images/AccuracyVsTime.png)


我的理解是 Residual 的构造更有利于保留底层的特征，所以在检测、分割等任务上泛化性更好。后续有一些针对检测的网络设计，如 MobileNet-V2, ShuffleNet, DetNet等, Resdual 构造基本上是标配了。


## 所以应该用哪个呢

为什么有的人使用 Inception 系列跑 baseline 而有的人使用 ResNet 系列呢？答：看习惯使用的深度学习框架。使用 TensorFlow 的人会顺手使用 Inception 系列跑 baseline，使用 Caffe、Caffe2、Pytorch 的 会顺手使用 ResNet 系列。就是这么简单的原因......

### 一点题外话

这篇博客写了个开头挖了坑之后，过了半年才补完。Anyway, better than nothing.


## 参考文献

[1][Rethinking the Inception Architecture for Computer Vision](https://arxiv.org/pdf/1512.00567.pdf)

[2][Speed/accuracy trade-offs for modern convolutional object detectors](https://arxiv.org/pdf/1611.10012.pdf)
