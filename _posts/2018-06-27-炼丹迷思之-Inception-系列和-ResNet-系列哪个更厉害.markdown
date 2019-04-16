---
published: true
---
## 前言

楼主近期换了一个环境炼丹，发现有新的分类任务时，这里的人习惯先用 Inception-V3 跑个 baseline 。而我之前总是习惯于用 ResNet-50 跑个 baseline 的。为什么会存在这样的差异呢？

## Inception 和 ResNet 系列对比

我对比了 Inception 系列 和 ResNet 系列论文里列出来的在 ImageNet 上的指标，感觉难以从指标上去衡量，毕竟模型的复杂度、图片分辨率、调参方式、评测时的crop方式等不太一致。根据周边小伙伴自己评测，ResNet-101 > Inception-V3 > ResNet-50的，基本上符合“越大的复杂度准确率越高”这个规律。

## 一点对论文的吐槽

别的且不说，就看 Inception-V3 的论文中为了刷高指标是怎么评估的：4个 Models, 144个 Crops 的 ensemble[my internal link][https://arxiv.org/pdf/1512.00567.pdf], 显得有点浮夸。相对来看 ResNet 的论文清爽很多。