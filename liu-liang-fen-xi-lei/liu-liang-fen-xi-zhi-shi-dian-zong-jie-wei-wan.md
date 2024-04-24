---
description: 我们将利用wireshark来讲解这一节的知识点介绍，因为就是用wireshark来分析，根本就无法脱离掉wireshark单独讲解。
---

# 🍔 流量分析知识点总结（未完）

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

### ②协议筛选

```
tcp     筛选协议为tcp的流量包
udp     筛选协议为udp的流量包
arp/icmp/http/ftp/dns/ip  筛选协议为arp/icmp/http/ftp/dns/ip的流量包
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

### ⑥源ip筛选

```
ip.src == 源ip地址
```

<figure><img src="../.gitbook/assets/image (3) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

或者我们点击Internet Protocol Version4下面的source 选中作为过滤器应用。

### ⑦目的ip筛选

```
ip.dst == 目的ip地址
```

<figure><img src="../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

另一种方法同理，选中作为过滤器。

### ⑧MAC地址筛选

```
eth.dst == 筛选目标mac地址
```

<figure><img src="../.gitbook/assets/image (2) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

```
eth.addr == 筛选MAC地址
```

<figure><img src="../.gitbook/assets/image (3) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

### ⑨端口筛选

```
tcp.dstport == 80 筛选tcp协议的目标端口
```

<figure><img src="../.gitbook/assets/image (4) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

同理

```
tcp.srcport == 筛选tcp协议源端口
```

```
udp.srcport == 筛选udp协议的源端口
```



### 1①包长度筛选

```
udp.length == 20 筛选长度为20的udp流量包
tcp.len >= **     筛选长度大于某个数的tcp流量包
ip.len == **      筛选长度为20的ip流量包
frame.len == **   筛选长度为20的整个流量包
```



### 1②http请求筛选

```
http.request.method == "GET"    筛选HTTP请求方式为GET
http.request.method == "POST"   筛选HTTP请求方式为POST
http.request.uri == "img/logo-ddu.gif"  筛选HTTP请求的URI为/img/logo-edu.gif
http contains "FLAG"             筛选HTTP内容为/FLAG 的流量包
```















***

## （3）wireshark 统计数据

最常用的就是对话数据的统计。

在统计->会话

<figure><img src="../.gitbook/assets/image (57).png" alt=""><figcaption></figcaption></figure>

我们可以从Rel Start去看从哪里开始，到哪里结束。

我们将一一介绍他们的统计作用。



### ①Protocol History（协议分级）

这个窗口实现的捕捉文件包含的所有协议的树状分支

<figure><img src="../.gitbook/assets/image (14) (1) (1).png" alt=""><figcaption></figcaption></figure>

包含的字段有

| 名称           | 	含义                     |
| ------------ | ----------------------- |
| Protocol：    | 协议名称                    |
| % Packets：   | 含有该协议的包数目在捕捉文件所有包所占的比例  |
| Packets：     | 含有该协议的包的数目              |
| Bytes：       | 含有该协议的字节数               |
| Mbit/s：      | 抓包时间内的协议带宽              |
| End Packets： | 该协议中的包的数目（作为文件中的最高协议层）  |
| End Bytes：   | 该协议中的字节数（作为文件中的最高协议层）   |
| End Mbit/s：  | 抓包时间内的协议带宽（作为文件中的最高协议层） |



### ②conversation（会话）

发生于一特定端点的IP间的所有流量。

<figure><img src="../.gitbook/assets/image (15) (1) (1).png" alt=""><figcaption></figcaption></figure>

查看收发大量数据流的 IP 地址。如果是你知道的服务器（你记得服务器的地址或地址范围），那问题就解决了；但也有可能只是某台设备正在扫描网络，或仅是一台产生过多数据的 PC。 ​ - 查看扫描模式（scan pattern）。这可能是一次正常的扫描，如 SNMP 软件发送 ping 报文以查找网络，但通常扫描都不是好事情





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

对于不能识别的，我们需要手动提取通过http传输的文件内容。

在分组详情中找到data，Line-based text，JPEG File Interchange Format，data：text/html层，然后鼠标右键点击->导出分组字节流。

<figure><img src="../.gitbook/assets/image (10) (1) (1).png" alt=""><figcaption></figcaption></figure>

如果是菜刀下载文件的流量，需要删除分组字节流前开头和结尾的X@Y字符，否则文件会出错。

右键->显示分组字节。然后再对弹出窗口的开始和结束进行修改。开始加三，结束减三。

<figure><img src="../.gitbook/assets/image (11) (1) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (12) (1) (1).png" alt=""><figcaption></figcaption></figure>











***

## （5）wireshark数据包搜索

ctrl+F，就能出来。

<figure><img src="../.gitbook/assets/image (5) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

这里有不同的过滤器能选，我们一般选择字符串。

<figure><img src="../.gitbook/assets/image (6) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

这里还有分组列表，分组详情，分组字节流三个选项，分别对应wireshark的三个部分。

<figure><img src="../.gitbook/assets/image (7) (1) (1).png" alt=""><figcaption></figcaption></figure>











***

## （6）数据包还原

wireshark的追踪流的功能可以将HTTP/TCP流量集合在一起还原成原始数据

右键->追踪流->HTTP流/TCP流

<figure><img src="../.gitbook/assets/image (8) (1) (1).png" alt=""><figcaption></figcaption></figure>

弹出的窗口可以看到被还原的流量信息。

<figure><img src="../.gitbook/assets/image (9) (1) (1).png" alt=""><figcaption></figcaption></figure>





***



## （7）总体步骤

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

## （8）PCAP文件修复

就是PCAP文件打开报错，就说明要修复。一般直接用工具pcapfix直接修复了。工具使用在流量分析工具里面。





***

## （9）对HTTPS协议分析

HTTPS是HTTP+SSL/TLS，所以我们传输的数据时加密后的数据。所以如果我们要得到真实的数据，需要导入SSL解密的密钥才能得到。











***

## （10）SMTP协议

筛选邮件的时候就可以用这个协议去筛选

> 简单邮件传输协议（SMTP）是一种通过网络传输电子邮件（[email](https://www.cloudflare.com/learning/email-security/what-is-email/)）的技术标准。与其他网络协议一样，SMTP 允许计算机和服务器交换数据，无论其底层硬件或软件是什么。正如使用信封地址书写的标准化格式允许邮政服务得以运作一样，SMTP 标准化电子邮件从发件人到收件人的传输方式，使广泛的电子邮件传递成为可能。











***

## （11）TLS解密

对于这个，可以先了解一下这篇文章所提到内容[https://zhangqingya.cn/2022/05/13/%E8%A7%A3%E5%AF%86TLS%E5%8D%8F%E8%AE%AE%E5%85%A8%E8%AE%B0%E5%BD%95%E4%B9%8B%E5%88%A9%E7%94%A8wireshark%E8%A7%A3%E5%AF%86](https://zhangqingya.cn/2022/05/13/%E8%A7%A3%E5%AF%86TLS%E5%8D%8F%E8%AE%AE%E5%85%A8%E8%AE%B0%E5%BD%95%E4%B9%8B%E5%88%A9%E7%94%A8wireshark%E8%A7%A3%E5%AF%86)

首先介绍什么是TLS，

TLS：

> 传输层安全性 （TLS） 在两个主机之间的通信中提供安全性。它提供完整性、身份验证和机密性。它最常用于 Web 浏览器，但可以与任何使用 TCP 作为传输层的协议一起使用。

目前wireshark提供了两种可以用的方法，一种是使用每个会话密钥的密钥日志文件（pre-master-secret），另一种是私钥解密。

### ①密钥交换算法

这个算法有一些主要的标志，比如ClientKeyExchange，Client hello，这种。

<figure><img src="../.gitbook/assets/image (66).png" alt=""><figcaption></figcaption></figure>

我们需要知道私钥文件的内容格式，例如

```
-----BEGIN PRIVATE KEY-----
MIIEvgIBADANBgkqhkiG9w0BAQEFAASCBKgwggSkAgEAAoIBAQDReQzlKVeAK8b5
TRcRBhSi9IYwHX8Nqc8K4HeDRvN7HiBQQP3bhUkVekdoXpRLYVuc7A8h1BLr93Qw
…
KOi8FZl+jhG+p8vtpK5ZAIyp
-----END PRIVATE KEY-----
```

我们如果要用它解密，只需要将这个文件，导入到编辑->首选项->协议->TLS->edit->+就可以了。

<figure><img src="../.gitbook/assets/image (67).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (68).png" alt=""><figcaption></figcaption></figure>

然后流量包就会被解密，再进行查找，就一般成功了。























## 参考门：







{% embed url="https://jwt1399.top/posts/29176.html" %}

{% embed url="https://ctf-wiki.org/misc/traffic/introduction/" %}
