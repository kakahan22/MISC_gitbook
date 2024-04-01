# 🤮 zip伪加密

就是把文件头的加密标志位做修改，进而打开文件。

## ①zip组成

zip由压缩源文件数据区，压缩源文件目录区，压缩源文件目录结束标志。

### Ⅰ压缩源文件数据区

头文件标记：

```
50 4B 03 04
```

<figure><img src=".gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

解压文件所需pkware版本

```
14 00
```

<figure><img src=".gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

全局方式位标记（有无加密）

```
00 00
```

<figure><img src=".gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

压缩方式

```
08 00
```

<figure><img src=".gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

最后修改文件时间

```
C2 64
```

<figure><img src=".gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

最后修改文件日期

```
66 4F
```

<figure><img src=".gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

CRC-32校验

```
C0 85 7E 7B
```

<figure><img src=".gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

压缩后尺寸

```
39 84 00 00
```

<figure><img src=".gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

未压缩尺寸

```
56 84 00 00
```

<figure><img src=".gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

文件名长度

```
05 00
```

<figure><img src=".gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

扩展记录长度

```
00 00
```

<figure><img src=".gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>



### Ⅱ压缩源文件目录区

目录中文件文件头标记

```
50 4B 01 02
```

这里可以利用查找功能进行查找，这个时候我们搜索完整语句的字是PK

<figure><img src=".gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>

然后结果里面的我们一个一个去看，大概第三个左右就是我们要找的

<figure><img src=".gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

压缩使用的pkware版本

```
1F 00
```

<figure><img src=".gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

解压需要的pkware版本

```
14 00
```

<figure><img src=".gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

全局方式位标记（有无加密，主要看这里，改为 09 00 或者 01 00就会提示有密码）

```
00 00
```

<figure><img src=".gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>





























