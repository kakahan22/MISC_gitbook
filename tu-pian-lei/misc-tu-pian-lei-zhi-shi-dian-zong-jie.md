---
description: 这里还有很多的工具所以我会把安装包也上传上来大家自行下载吧。也有一个博主已经弄了一个把他们都集成的工具我也懒得再来弄一次。
---

# 🌍 MISC图片类知识点总结

## <mark style="color:red;">1.文件格式分析</mark>

我们先按按照文件格式来对不同类型的图片的格式进行分析后面进行总结。

对于格式的分析建议下载winhex来进行分析和学习。安装包在首页可以自取。

首先介绍png的文件格式

### <mark style="color:orange;">①png</mark>

将一张png图片放到winhex下面看看吧。

<figure><img src="../.gitbook/assets/image (2) (1).png" alt=""><figcaption></figcaption></figure>

#### <mark style="color:yellow;">(1)png文件格式</mark>

png文件从整体上来看主要是由文件头和三组以上的数据块（后面介绍）按照特定的顺序组成，最基本的png至少包括文件头，IHDR,IDAT,IEND组成。用一张图来表示

<figure><img src="../.gitbook/assets/image (3) (1).png" alt=""><figcaption></figcaption></figure>

### <mark style="background-color:red;">Ⅰ.文件头</mark>

前面的文件头就是下面的

```
89 50 4E 47 0D 0A 1A 0A          
```

<figure><img src="../.gitbook/assets/image (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

### <mark style="background-color:red;">Ⅱ数据块（Chunk）</mark>

PNG有两种类型的数据块，一个是标准的数据块，另外一个是辅助数据块，我们这里介绍关键数据块，就是我们前面图片中提到的IHDR,PLTE,IDAT,IEND。

数据块又是由length，Chunk Type Code（数据类型码），Chunk Data，CRC（循环冗余检测组成）。

它们的长度和作用由下面来表示。

| 名称                      | 字节数  | 说明                             |
| ----------------------- | ---- | ------------------------------ |
| Length（长度）              | 4字节  | 指定数据块中数据域的长度，其长度不超过（2^31-1)个字节 |
| Chunk Type Code（数据块类型码） | 4字节  | 数据块类型码由ASCII字母组成               |
| Chunk Data（数据块数据）       | 可变长度 | 按照Chunk Type Code指定的数据储存       |
| CRC（循环冗余检测）             | 4字节  | 用来检测是否有错误                      |

#### ①length：

<figure><img src="../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

这个长度是13个字节，一般都是13个字节。表示头部数据块的长度为13（从宽高开始算）

#### ②CRC

<figure><img src="../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

从第二行的D开始后4个字节就是CRC校验码。

其中CRC是通过对Chunk Data和Chunk Type Code计算得到的。

#### <mark style="background-color:orange;">（1）CRC结果获得方式：</mark>

#### ①method1：CRC校验值计算脚本

```python
import zlib

with open('路径','rb') as image_data:
    bin_data = image_data.read()
#截取待计算的字符串即IHDR中去除前四字节（length）和后四字节（CRC）
data = bytearray(bin_data[12:29])
#使用函数计算
crc32key = zlib.crc32(data)
print(hex(crc32key))

```

#### ②method2：在线网站

{% embed url="http://www.ip33.com/crc.html" %}

{% embed url="https://www.lddgo.net/encrypt/crc" %}





### <mark style="background-color:red;">Ⅲ.IHDR</mark>

这个IHDR是我们会需要知道的。包含了PNG文件中存储的图像数据的基本信息。是文件头之后的第一个数据块。文件头数据块是由13个字节组成的。（这里常常会考改变高度或者宽度来把隐藏的信息显示出来）

我们还是通过WINHEX来介绍。IHDR的16进制是下面的

```
49 48 44 52
```

<figure><img src="../.gitbook/assets/image (4) (1).png" alt=""><figcaption></figcaption></figure>

然后后面就是她的主要内容，一共是13个字节。他的格式网上有表格总结，这里贴过来。我们主要关注前8字节

| 域的名称    | 字节数      | 说明           |
| ------- | -------- | ------------ |
| Width   | 4 bytes  |  图像宽度，以像素为单位 |
| Height  | 4 bytes  | 图像高度，以像素为单位  |

比如在这个winhex里面width为

<figure><img src="../.gitbook/assets/image (5) (1).png" alt=""><figcaption></figcaption></figure>

height为

<figure><img src="../.gitbook/assets/image (6) (1).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
文件的height和weight不能随意修改。
{% endhint %}

需要根据CRC修改。

根据CRC爆破图片宽度和高度脚本

```python
import zlib
import struct
import argparse
import itertools


parser = argparse.ArgumentParser()
parser.add_argument("-f", type=str, default=None, required=True,
                    help="输入同级目录下图片的名称")
args  = parser.parse_args()


bin_data = open(args.f, 'rb').read()
crc32key = zlib.crc32(bin_data[12:29]) # 计算crc
original_crc32 = int(bin_data[29:33].hex(), 16) # 原始crc


if crc32key == original_crc32: # 计算crc对比原始crc
    print('宽高没有问题!')
else:
    input_ = input("宽高被改了, 是否CRC爆破宽高? (Y/n):")
    if input_ not in ["Y", "y", ""]:
        exit()
    else: 
        for i, j in itertools.product(range(4095), range(4095)): # 理论上0x FF FF FF FF，但考虑到屏幕实际/cpu，0x 0F FF就差不多了，也就是4095宽度和高度
            data = bin_data[12:16] + struct.pack('>i', i) + struct.pack('>i', j) + bin_data[24:29]
            crc32 = zlib.crc32(data)
            if(crc32 == original_crc32): # 计算当图片大小为i:j时的CRC校验值，与图片中的CRC比较，当相同，则图片大小已经确定
                print(f"\nCRC32: {hex(original_crc32)}")
                print(f"宽度: {i}, hex: {hex(i)}")
                print(f"高度: {j}, hex: {hex(j)}")
                exit(0)

```



### <mark style="background-color:red;">Ⅳ.PLTE</mark>

调色板数据块 PLTE（palette chunk）：它包含有与索引彩色图像（indexed-color image）相关的彩色变换数据，它仅与索引彩色图像有关，而且要放在图像数据块（image data chunk）之前。

| 颜色    | 字节 | 意义              |
| ----- | -- | --------------- |
| red   | 1  | 0 = 黑色, 255 = 红 |
| green | 1  | 0 = 黑色, 255 = 绿 |
| blue  | 1  | 0 = 黑色, 255 = 蓝 |

因为三原色的原因，调色板数据块的长度应该是三的倍数，否则就是一个非法调色板。



### <mark style="background-color:red;">Ⅵ.IDAT</mark>

它存储实际的数据，在数据流中可包含多个连续顺序的图像数据块。

IDAT存放着图像真正的数据信息，因此，如果能够了解IDAT的结构，我们就可以很方便的生成PNG图像。

* 储存图像像数数据
* 在数据流中可包含多个连续顺序的图像数据块
* <mark style="color:yellow;">采用 LZ77 算法的派生算法进行压缩</mark>
* <mark style="color:yellow;">可以用 zlib 解压缩</mark>

{% hint style="info" %}
值得注意的是，IDAT 块只有当上一个块充满时，才会继续一个新的块。
{% endhint %}

所以当出现IDAT不满出错时，大部分是有隐写，我们从中可以得到flag。

这里有一个工具可以判断IDAT是否是正确的。pngcheck ，如果不了解的，可以去看看。 [tu-pian-lei-gong-ju-zong-jie.md](tu-pian-lei-gong-ju-zong-jie.md "mention")

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

我们可以看到我的这张图片的IDAT的长度是在65536就满了。

这里展示一个利用python zlib解压多余IDAT块的内容的脚本，注意剔除长度，数据块类型以及末尾的CRC检验值

```python
import zlib
import binascii
IDAT = "789...667".decode('hex')
result = binascii.hexlify(zlib.decompress(IDAT))
print result
```

这里还有一个知识点LSB

## <mark style="color:yellow;">①LSB</mark>

我们需要用到一个非常常用的工具叫做，stegsolve。 [tu-pian-lei-gong-ju-zong-jie.md](tu-pian-lei-gong-ju-zong-jie.md "mention")

> LSB：
>
> &#x20;Least Significant Bit，最低有效位。PNG 文件中的图像像数一般是由 RGB 三原色（红绿蓝）组成，每一种颜色占用 8 位，取值范围为 `0x00` 至 `0xFF`，即有 256 种颜色，一共包含了 256 的 3 次方的颜色，即 16777216 种颜色。
>
> 而人类的眼睛可以区分约 1000 万种不同的颜色，意味着人类的眼睛无法区分余下的颜色大约有 6777216 种。
>
> LSB 隐写就是修改 RGB 颜色分量的最低二进制位（LSB），每个颜色会有 8 bit，LSB 隐写就是修改了像数中的最低的 1 bit，而人类的眼睛不会注意到这前后的变化，每个像素可以携带 3 比特的信息。

### <mark style="background-color:red;">Ⅴ.IED</mark>

文件尾部表示图像结束。

```
00 00 00 00 49 45 4E 44 AE 42 60 82
```

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

IEND数据块的长度总是`00 00 00 00`，数据标志总是`49 45 4E 44` ，所以他的CRC码也总是`AE 42 60 82`

***

### ②JPG

先将一张JPG图片放到winhex下面看看。

<figure><img src="../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
jpg和jpeg都是一样的，没有区别。
{% endhint %}

jpg格式的文件是分为一个一个的段里存储的，段的多少和长度并不是一定的。每个段一定都包括短的标志和类型，段的长度。就是这么理解，jpg就是一段段的，每一段开头都有一个标志。

### <mark style="background-color:red;">Ⅰ.段的标识与类型</mark>

不同的段的段类型不同，但是一张图片的开头的段都是SOI类型

| 段类型  | 表示符号    | 说明                 |
| ---- | ------- | ------------------ |
| SOI  | `FF D8` | 文件头                |
| APP0 | `FF E0` | 定义交换格式和图像识别信息      |
| APP1 | `FF E1` | 定义交换格式和图像识别信息      |
| ……   | ……      | ……                 |
| APPn | `FF En` | 定义交换格式和图像识别信息      |
| DQT  | `FF DB` | 定义量化表              |
| SOF0 | `FF C0` | 图像基本信息             |
| SOF1 | `FF C1` | 图像基本信息             |
| ……   | ……      | ……                 |
| SOFn | `FF Cn` | 图像基本信息             |
| DHT  | `FF C4` | 定义 Huffman 表（霍夫曼表） |
| DRI  | `FF DD` | 定义重新开始间隔           |
| SOS  | `FF DA` | 扫描行开始              |
| COM  | `FF FE` | 注释                 |
| EOI  | `FF D9` | 文件尾                |













## 参考门：

{% embed url="https://blog.51cto.com/baimao/6753494" %}

{% embed url="https://www.cnblogs.com/grayi/p/15203516.html" %}

{% embed url="https://ctf-wiki.org/misc/picture/png/" %}

{% embed url="https://www.cnblogs.com/P201821460033/p/13658489.html" %}











