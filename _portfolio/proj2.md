---
title: "Geek: A Simple COVID-19 Kinetic Simulation Model"
subtitle: Lorem ipsum dolor sit amet consectetur.
image: assets/img/portfolio/proj2/2.11-SEIRD2.png
alt: Keep Exploring

caption:
  title: "Geek: A Simple COVID-19 Kinetic Simulation Model(2020)"
  subtitle: A kinetic model with ode-like functions predicting the COVID-19 trend.
  thumbnail: assets/img/portfolio/proj2/header0.jpeg
---
[Original Passage in Chinese](https://mp.weixin.qq.com/s/MeH9_ctKkoeE6pyKV-dOCw)


我的小破号已经死了一个多月了，除了一些照片分享就没再发过一些新奇好玩而荒谬的事情，现在终于有机会啦！

这本是一篇放了一个多月的推送草稿。早在2月初，我就已经开始给病毒传播进行动力学建模了。但当时正值疫情最严重的的时候，放出一系列“令人堪忧”的预测数据就算连手动狗头也不能保命了，而且当时数据也相当不够，还有非常多问题没有解决，不过，当时确实成功提前12天预测到了中国疫情的高峰。现在，疫情在全球范围内传播，这又给了我很多新的数据，于是我决定重启这个计划。

# Set up of the mathematical model
Let's devide the population into several parts: sustainable, exposed, infected, recovered and dead. This is the so-called SEIRD kinectic model.

![avatar](assets/img/portfolio/proj2/SER模型示意图.png){:width="100%"}