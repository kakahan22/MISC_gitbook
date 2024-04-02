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

<figure><img src="../.gitbook/assets/image (9) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

## 2.stegsolve

### （1）官方文档下载方法

{% embed url="https://wiki.bi0s.in/steganography/stegsolve/" %}

### （2）使用方法

这里也是在linux环境下面的。这是一款图像隐写神奇可以这么说。

我们首先介绍他的界面的功能

<figure><img src="../.gitbook/assets/image (3) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

File Format：文件格式，查看图片的具体信息

Data Extract：数据抽取，图片中隐藏数据的抽取

Frame Browser：帧浏览器，主要是对GIF之类的动图进行分解。

Image Combiner：拼图，图片拼接。



### ①File Format：

查看文件格式

<figure><img src="../.gitbook/assets/image (4) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

我们可以看到他有Chunk数据块的很多信息，CRC什么的都有。



### ②Data Extract

数据提取

<figure><img src="../.gitbook/assets/image (5) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

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

<figure><img src="../.gitbook/assets/image (6) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

## 3.Stegdetect

### （1）官方文档下载方法

{% embed url="https://wiki.bi0s.in/steganography/stegdetect/" %}

{% file src="../.gitbook/assets/Stegdetect.zip" %}



### （2）使用方法

直接用可视化的方式，打开xsteg.exe。

<figure><img src="../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

然后修改参数，把sensitivity修改为10.00,把敏感度调高了才好检测到隐藏信息。

然后选择文件

<figure><img src="../.gitbook/assets/image (2) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

就可以出现结果了。

也可以用指令。

```
-q 仅显示可能包含隐藏内容的图像。
-n 启用检查JPEG文件头功能，以降低误报率。如果启用，所有带有批注区域的文件将被视为没有被嵌入信息。如果JPEG文件的JFIF标识符中的版本号不是1.1，则禁用OutGuess检测。
-s 修改检测算法的敏感度，该值的默认值为1。检测结果的匹配度与检测算法的敏感度成正比，算法敏感度的值越大，检测出的可疑文件包含敏感信息的可能性越大。
-d 打印带行号的调试信息。
-t 设置要检测哪些隐写工具（默认检测jopi），可设置的选项如下：
j 检测图像中的信息是否是用jsteg嵌入的。
o 检测图像中的信息是否是用outguess嵌入的。
p 检测图像中的信息是否是用jphide嵌入的。
i 检测图像中的信息是否是用invisible secrets嵌入的。
```

***

## 4.convert

### (1)下载

```
sudo apt-get install imagemagick
```

### （2）使用方法

用来对gif图片进行操作，可以把每一帧截出来，也可以把图片拼接在一起。

#### ①分离gif文件。

```
convert A.gif A.png  #将A.gif中每一帧提取成A-n.png
```

<figure><img src="../.gitbook/assets/image (6) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (7) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

答应我在一个文件夹里面弄，不然会弄死你。

#### ②拼接图片

```
convert [参数1] {输入文件名} [输出文件名]		#拼接
#[参数1]：+append 横向拼接 -append 纵向拼接 
#{输入文件名}：要拼接的图片，每张图片名之间用空格分隔，支持正则表达式，有先后顺序
```

***

## 5.identify

以通过 **identify** 命令清晰的打印出每一帧的时间间隔。

```
identify -format "%s %T \n" 100.gif  	#格式：帧序号 间隔
```

***

## 6.exiftool

### （1）官方文档下载方式

{% embed url="https://exiftool.org/" %}

### （2）使用方法

这里是linux环境下，直接查看信息就是

```
exiftool a.jpg
```

<figure><img src="../.gitbook/assets/image (8) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

## 7.binwalk

### （1）官方文档

{% embed url="https://www.kali.org/tools/binwalk/" %}

### （2）使用方法

_Binwalk 是一种快速、易于使用的工具，用于分析、逆向工程和提取固件映像。其实就是分析文件组成。_

#### ①分析文件组成

<figure><img src="../.gitbook/assets/image (10) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

#### ②分离文件

```
dd if=raw.jpg of=1.zip skip=xxx bs=1
```

***

## 8.formost

### （1）官方文档

{% embed url="https://www.kali.org/tools/foremost/" %}

### （2）使用方法

将所有文件全部分离。一锅端。

```
foremost 1.jpg
```

***

## 9.file

### （1）官方文档

{% embed url="https://blog.csdn.net/TCatTime/article/details/113812754" %}

### （2）使用方法

file的功能很强大，就是探测文件内部，并决定什么类型。除此之外，他还能告诉我们编码的类型，链接文件地址，是否为可执行脚本。

```
file 文件名
```

<figure><img src="../.gitbook/assets/image (12) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

## 10.bwm

### （1）官方文档

{% embed url="https://linux.die.net/man/1/bwm-ng" %}

### （2）使用方法

这里用的kali真的方便到爆炸。

盲水印主要有加密和解密两种指令。

### ①加密

```sh
bwm encode 1.png water.png 2.png
//1.png 为无水印原图
//water.png 为水印图
//2.png 为有盲水印图
```

### ②解密

```
bwm decode 1.png 2.png flag.png
//1.png 为无水印原图
//2.png 为有盲水印的图
// flag.png 为解出来的图片
```

***

## 11.strings

### （1）官方文档

{% embed url="https://ipcmen.com/strings" %}

### （2）使用方法



就是查找可以打印的字符。其实这个感觉输出的内容就是可以用winhex来看。

```
strings 文件名
```

<figure><img src="../.gitbook/assets/image (13) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

## 12.eog

这个就是linux下查看图片的指令。不然每次去文件夹里面打开太复杂了。

```
eog 图片
```

***

## 13.F5-steganography

### ①文档介绍

就是图片F5隐写的工具。

{% embed url="https://github.com/matthewgao/F5-steganography" %}

注意java版本得一样，不然就要换版本

### ②使用方法

指令，到工具目录下去执行，解密完的图片就在output.txt当中

```
java Extract 图片的绝对路径.jpg
```

<figure><img src="../.gitbook/assets/image (19).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>



















## 参考门：

{% embed url="https://www.cnblogs.com/lzkalislw/p/13475137.html" %}

{% embed url="https://cloud.tencent.com/developer/article/2272480" %}









