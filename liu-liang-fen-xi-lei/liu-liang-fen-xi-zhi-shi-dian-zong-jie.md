---
description: 我们将利用wireshark来讲解这一节的知识点介绍，因为就是用wireshark来分析，根本就无法脱离掉wireshark单独讲解。
---

# 🍔 流量分析知识点总结

{% embed url="https://www.youtube.com/watch?v=xdQ9sgpkrX8" %}

## （1）用wireshark解释TCP/IP

### ①TCP三次握手，四次挥手

<figure><img src="../.gitbook/assets/image (45).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (46).png" alt=""><figcaption></figcaption></figure>

我们习惯将第一个TCP协议用红色标记出来。

<figure><img src="../.gitbook/assets/image (47).png" alt=""><figcaption></figcaption></figure>

我们查看具体信息。

<figure><img src="../.gitbook/assets/image (48).png" alt=""><figcaption></figcaption></figure>

我们可以看到source port，Destionation port，

上面的stream index：0就是说明一个流的开始。这里你可以看到你有多少个tcp流。

sequence number是随着我们发送的数据而递增的数据。如果sequence number增加1那就是我们已经发送了一个字节的数据。

Window size value：就是一次能最多传送多少数据量。

<figure><img src="../.gitbook/assets/image (49).png" alt=""><figcaption></figcaption></figure>

TCP options：这里是制定规则的地方。

no operations：确保他的字节数是4的倍数

***

## （2）wireshark过滤器

### ①过滤ip地址

```
ip.addr == 192.168.......
```

<figure><img src="../.gitbook/assets/image (51).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
我们还可以右键继续过滤，比如是需要ipv4，ipv6，之类的。
{% endhint %}

### ②过滤tcp

```
tcp
```

<figure><img src="../.gitbook/assets/image (52).png" alt=""><figcaption></figcaption></figure>

我们也可以用下面的标头去作为过滤器，右键让他被选中就可以。

### ③排除某些

```
not 某些规则
```

<figure><img src="../.gitbook/assets/image (53).png" alt=""><figcaption></figcaption></figure>

### ④tcp端口

如果我们想表示tcp端口在某些选项里面，我们可以

```
tcp.port in {80 443 8080}
```

<figure><img src="../.gitbook/assets/image (54).png" alt=""><figcaption></figcaption></figure>

### ⑤框架选择

如果我们想知道某些的密码或者有用的字符串，我们可以先过滤出某些框架里面包含这个字符串的包（这里没有google和baidu）

```
frame contains baidu
```

<figure><img src="../.gitbook/assets/image (55).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
contani区分大小写，match不区分大小写
{% endhint %}





***

## （3）wireshark 统计数据

最常用的就是对话数据的统计。

在统计->会话

<figure><img src="../.gitbook/assets/image (57).png" alt=""><figcaption></figcaption></figure>

我们可以从Rel Start去看从哪里开始，到哪里结束。



***

## （4）从wireshark中提取文件

一般是看_**http协议**_可以看到访问的内容。

<figure><img src="../.gitbook/assets/image (58).png" alt=""><figcaption></figcaption></figure>

可以看到他访问的php文件，他的密码之类的。

我们一般要导出的文件类型有六种，在文件->导出对象下。有DICOM ,HTTP,FTP-DATA,TFTP,SMB

一般wireshark能为我们自动识别这些，比如我们选择HTTP

<figure><img src="../.gitbook/assets/image (59).png" alt=""><figcaption></figcaption></figure>

他识别出了图片之类的。我们选择保存然后查看图片。

<figure><img src="../.gitbook/assets/image (60).png" alt=""><figcaption></figcaption></figure>

对于不能识别的，我们需要选择_**追踪流->tcp协议**_

自行查看是否有文件。



***

## 总体步骤

上述主要是对wireshark进行简单的利用的介绍，接下来介绍流量包分析的具体方法步骤。

步骤主要是

* 总体把握
  * 协议分级
  * 端点统计
* 过滤赛选
  * 过滤语法
  * Host，Protocol，contains，特征值
* 发现异常
  * 特殊字符串
  * 协议某字段
  * flag 位于服务器中
* 数据提取
  * 字符串取
  * 文件提取

赛题就分为

* 流量包修复
* 协议分析
* 数据提取



我们知识点也从上述方面来讲解。





***











## 参考门：

{% embed url="https://ctf-wiki.org/misc/traffic/introduction/" %}
