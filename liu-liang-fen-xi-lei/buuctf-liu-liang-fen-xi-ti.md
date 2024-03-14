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

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

直接交上去成功了。



***

## 4.大流量分析（二） 1

这里有个知识点补充就是smtp协议

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

直接就找到了from。

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>





***

## 5.大流量分析（三） 1













