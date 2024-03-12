---
description: Misc感觉就是在用工具，发现有点难了说实话，比web还难入门一点。
---

# 🪐 图片类工具总结



## 1.pngcheck

### （1）官方文档下载方法

{% embed url="https://wiki.bi0s.in/steganography/pngcheck/" %}

### (2)使用方法

这里是在linux环境下。主要是为了显示文件是否损坏，显示大小，类型，压缩信息的工具。

这个比较简单，只有一个常用指令。

```sh
pngcheck -v 图片名
```

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

***

## 2.stegsolve

### （1）官方文档下载方法

{% embed url="https://wiki.bi0s.in/steganography/stegsolve/" %}

### （2）使用方法

这里也是在linux环境下面的。这是一款图像隐写神奇可以这么说。

我们首先介绍他的界面的功能

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

File Format：文件格式，查看图片的具体信息

Data Extract：数据抽取，图片中隐藏数据的抽取

Frame Browser：帧浏览器，主要是对GIF之类的动图进行分解。

Image Combiner：拼图，图片拼接。



### ①File Format：

查看文件格式

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

我们可以看到他有Chunk数据块的很多信息，CRC什么的都有。



### ②Data Extract

数据提取

<figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

左边主要是RGBA的颜色通道。我们先介绍这几个参数。

1.Alpha（透明度）：该通道用256级灰度来记录图像中的透明度信息，定义透明、不透明和半透明区域

alpha的值为0就是全透明，alpha 的值为 255 则表示不透明

2.RGB（红绿蓝）：代表亮度。R的数字越大，则代表红色亮度越高；R的数字越小，则代表红色亮度越低。G，B同理。

R的亮度各有256个级别，GB同理。即从0到255，合计为256个。从数字0到255的逐渐增高，我们人眼观察到的就是亮度越来越大，红色、绿色或蓝色越来越亮。

但是这里主要是为了LSB隐写。

3..Extra By(额外的)：分为row（行）和column（纵），每个像素用R，G，B三个分量表示，那么一张图片就像一个矩阵，矩阵的每个单位就是（0\~255，0\~255，0\~255），也就会有是纵排列和行排列了，一般事先访问行再访问列（如果相反会引起ve使用方法）。

4..Bit Order（位顺序）:MSB是一串数据的最高位，LSB是一串数据的最低位。



### <mark style="color:red;">LSB隐写：</mark>

而LSB隐写就是修改RGB颜色分量的最低二进制位也就是最低有效位（LSB），而人类的眼睛不会注意到这前后的变化，（人类的眼睛只能识别一部分颜色的变化）

所以我们如果要看到LSB隐写的信息的话，就要把他设置成为下图这样。

<figure><img src="../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>





















## 参考门：

{% embed url="https://www.cnblogs.com/lzkalislw/p/13475137.html" %}

