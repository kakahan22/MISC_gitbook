---
description: 这里是通过一个课程youtube上面的课程来做这个wireshark的教程使用，虽然已经学了很多遍了，但是总感觉因为没有学计算机网络，所以理解的没那么好。
---

# 🍟 流量分析工具wireshark

{% embed url="https://www.youtube.com/watch?v=OU-A2EmVrKQ&list=PLW8bTPfXNGdC5Co0VnBK1yVzAwSSphzpJ" %}

这里用的流量包是

{% file src="../.gitbook/assets/dianli_jbctf_MISC_T10075_20150707_wireshark.pcap" %}

***



<figure><img src="../.gitbook/assets/image (36).png" alt=""><figcaption></figcaption></figure>

## 1.时间内容更改

我们可以把time改成其他形式。

```
视图->时间显示格式
```

<figure><img src="../.gitbook/assets/image (37).png" alt=""><figcaption></figcaption></figure>

比如我们想把他设置成年月日。然后就变成了

<figure><img src="../.gitbook/assets/image (38).png" alt=""><figcaption></figcaption></figure>

***

## 2.着色

不同的协议以及错误之类的，用不同的颜色表示。我们也可以自己设置自己的颜色协议。

```
视图->着色规则
```

<figure><img src="../.gitbook/assets/image (39).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (40).png" alt=""><figcaption></figcaption></figure>

我们可以看到在我的电脑上，错误的TCP协议是红色的字，HTTP协议是绿色的底。



***

## （3）过滤带有某些内容的数据包

首先选择某些包，然后假如我们对syn进行过滤。

那么选择到他的syn，然后右键，

```
准备作为过滤器->选中
```

<figure><img src="../.gitbook/assets/image (41).png" alt=""><figcaption></figcaption></figure>

然后就会在过滤器栏里面出现

<figure><img src="../.gitbook/assets/image (42).png" alt=""><figcaption></figcaption></figure>

然后确定，就能看到跟踪的包的路径。

<figure><img src="../.gitbook/assets/image (43).png" alt=""><figcaption></figcaption></figure>

如果我们想专门对某些包里面的内容过滤，我们需要点击那个加号，

<figure><img src="../.gitbook/assets/image (44).png" alt=""><figcaption></figcaption></figure>

如果要删除某些条件，我们右键然后选择移除或者其他的情况。



***

























