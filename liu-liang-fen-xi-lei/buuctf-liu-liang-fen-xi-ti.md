# 🌯 BUUCTF流量分析题

## 1.被嗅探的流量 1

直接字符串搜索出来flag。

<figure><img src="../.gitbook/assets/image (62).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (63).png" alt=""><figcaption></figcaption></figure>



***

## 2.wireshark 1

管理员的密码就是flag，那我们查看一下http，会不会有线索

<figure><img src="../.gitbook/assets/image (64).png" alt=""><figcaption></figcaption></figure>

直接字符搜索pass

<figure><img src="../.gitbook/assets/image (65).png" alt=""><figcaption></figcaption></figure>

得到flag。



***

## 3.大流量分析（一） 1

直接看第一个包发现黑客在目录穿越

<figure><img src="../.gitbook/assets/image (3) (1) (1).png" alt=""><figcaption></figcaption></figure>

直接交上去成功了。



***

## 4.大流量分析（二） 1

这里有个知识点补充就是smtp协议

<figure><img src="../.gitbook/assets/image (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

直接就找到了from。

<figure><img src="../.gitbook/assets/image (2) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>





***

## 5.大流量分析（三） 1

找后门文件

就是找



***

## 6.\[NewStarCTF 2023 公开赛道]流量！鲨鱼！ 19

<figure><img src="../.gitbook/assets/image (6) (1).png" alt=""><figcaption></figcaption></figure>

直接在导出对象里面根据大小去找会快很多

<figure><img src="../.gitbook/assets/image (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

看到base64加密知道就应该对了，两次，出来flag

<figure><img src="../.gitbook/assets/image (2) (1) (1).png" alt=""><figcaption></figcaption></figure>





***

## 7.\[DDCTF2018]流量分析 1

这里是一道有关TSL密钥的题目，目前做到的唯一一道。

先去到处对象里面找到邮件，查看邮件的内容

<figure><img src="../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

查找着就看到了一个图片，查看一下图片的内容，

<figure><img src="../.gitbook/assets/image (25).png" alt=""><figcaption></figcaption></figure>

然后猜测应该是OCR文字识别，然后把他加到密钥文件里面。

<figure><img src="../.gitbook/assets/image (2) (1).png" alt=""><figcaption></figcaption></figure>

记得识别出来的要改0和o还有空集

<figure><img src="../.gitbook/assets/image (4) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (5) (1).png" alt=""><figcaption></figcaption></figure>





















