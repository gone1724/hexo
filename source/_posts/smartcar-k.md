---
title: 小单车，我们走
date: 2021-05-18 18:51:41
updated: 2021-06-18 15:51:41
categories:
- 智能车
tags:
- 经验分享
- 开源
sticky:
comments: true
toc: false
---

> 2021智能车单车组开源。

今天就拿GitHub的一个项目水一篇~

本人参与硬件部分，不过也是新手。把自己的硬件部分开源，希望和大家一起交流进步。好多资料网络上都可以查得到的，可以认为这里做的是硬件方案的分享。
<!-- more -->

本篇博客更新截至`2021.6.18`，最新请前往[GitHub项目地址](https://github.com/gone1724/Smartcar_K)。

***********

# 2021-3-20
先上传前期的一套方案的原理图，目前遇到的问题是主板模块下载程序成功率较低。
可能是MCU供电和USB转TTL电压因为分开供电，电压不稳造成的。

# 2021-3-22
究极一体板方案！（bushi）这是最近尝试的一体板方案，包括全桥驱动芯片和四电感运放部分，希望不要出问题。

# 2021-4-7
MCU V3.1的驱动部分，8V稳压好像只能到7.1V。

# 2021-5-17
把主板上稳压去掉了，用的之前的驱动板驱动，几个月了，稳的一批。
不过我现在的2350运放又出问题了，之前还能用，现在咋用不了了

# 2021-5-20

运放没问题，是电磁杆焊的有问题，FPC好难焊得好啊。

# 2021-6-6

只能暂时说再见了！我们最后代码已经上传，只做到了单车的直线前进。不能转圈的原因，学长说可能滤波效果没做好之类，不管了。