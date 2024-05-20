---
description: 要参加这个比赛前还是得先做个题。
---

# 2023盘古石晋级赛

## Android程序分析

### 1.涉案应用刷刷樂的签名序列号是\[答案：123ca12a]\[★☆☆☆☆]

```
11fcf899
```

直接放到jadx里面

<figure><img src="../.gitbook/assets/image (94).png" alt=""><figcaption></figcaption></figure>







### 2.涉案应用刷刷樂是否包含读取短信权限\[答案：是/否]\[★★☆☆☆] 1 否&#x20;

可以看到main文件里面不包括，read没有读短信的

```
否
```

<figure><img src="../.gitbook/assets/image (95).png" alt=""><figcaption></figcaption></figure>





### 3.涉案应用刷刷樂打包封装的调证ID值是\[答案：123ca12a]\[★★☆☆☆] 1 A6021386163125&#x20;

在complier包里面的APPID就是调证ID值

```
A6021386163125
```

<figure><img src="../.gitbook/assets/image (96).png" alt=""><figcaption></figcaption></figure>



### 4.涉案应用刷刷樂服务器地址域名是\[答案：axa.baidun.com]\[★★★☆☆] 2 vip.shuadan.com&#x20;

在index.html文件里面有服务器地址域名

```
vip.shuadan.com
```

<figure><img src="../.gitbook/assets/image (97).png" alt=""><figcaption></figcaption></figure>







### 5.涉案应用刷刷樂是否存在录音行为\[答案：是/否]\[★★★☆☆] 2 是&#x20;

可以搜索audiomanager查看代码看是否存在

```
​是
```

<figure><img src="../.gitbook/assets/image (98).png" alt=""><figcaption></figcaption></figure>

可以看到是有的，但是被隐藏了。

<figure><img src="../.gitbook/assets/image (99).png" alt=""><figcaption></figcaption></figure>





### 6.涉案应用未来资产的包名是\[答案：axa.baidun.com]\[★☆☆☆☆] 1 plus.H5CE4B30D&#x20;

```
plus.H5CE4B30D
```



<figure><img src="../.gitbook/assets/image (100).png" alt=""><figcaption></figcaption></figure>



### 7.涉案应用未来资产的语音识别服务的调证key值是\[答案：1ca2jc]\[★★☆☆☆] 1 53feacdd&#x20;

后来知道第三方都在main文件里面的activity标签就对应一个。

```
53feacdd
```



<figure><img src="../.gitbook/assets/image (101).png" alt=""><figcaption></figcaption></figure>



### 8.涉案应用未来资产的服务器地址域名是\[答案：axa.baidun.com]\[★★★☆☆] 2 vip.usdtre.club&#x20;

和index.html在一起的文件的位置下面

```
vip.usdtre.club
```

<figure><img src="../.gitbook/assets/image (102).png" alt=""><figcaption></figcaption></figure>



### 9.涉案应用未来资产的打包封装的调证ID值是是\[答案：axa.baidun.com]\[★★☆☆☆]

```
h5ce4b30d
```

<figure><img src="../.gitbook/assets/image (103).png" alt=""><figcaption></figcaption></figure>









***

## 移动智能终端取证

### 1.根据容恨寒的安卓手机分析，手机的蓝牙物理地址是\[答案：B9:8B:35:8B:03:52]\[★☆☆☆☆] 1 A9:8B:34:8B:04:50&#x20;

直接取证跑出来。

```
A9:8B:34:8B:04:50
```

<figure><img src="../.gitbook/assets/image (63).png" alt=""><figcaption></figcaption></figure>





### 2.根据容恨寒的安卓手机分析，SIM卡的ICCID是\[答案：80891103212348510720]\[★☆☆☆☆] 1 89014103211118510720&#x20;



```
89014103211118510720
```

<figure><img src="../.gitbook/assets/image (64).png" alt=""><figcaption></figcaption></figure>







### 3.根据容恨寒的安卓手机分析，团队内部沟通的聊天工具程序名称是\[答案：微信]\[★☆☆☆☆] 1 Potato&#x20;

之前看到有人问为什么是，其实感觉其他的知道的都不是，这个一搜就知道是聊天软件。

```
Potato
```

<figure><img src="../.gitbook/assets/image (65).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (66).png" alt=""><figcaption></figcaption></figure>







### 4.根据容恨寒的安卓手机分析，团队内部沟通容恨寒收到的最后一条聊天信息内容是\[答案：好的]\[★★★☆☆] 2 收到&#x20;

这个要去数据库里面去看了，因为取证软件没有取证出来。直接跳转失败的，可以用7zip去直接找到文件目录然后打开。

```
收到
```

<figure><img src="../.gitbook/assets/image (67).png" alt=""><figcaption></figcaption></figure>

group应该是g

<figure><img src="../.gitbook/assets/image (68).png" alt=""><figcaption></figcaption></figure>

把时间戳的时间升序排列一下

<figure><img src="../.gitbook/assets/image (70).png" alt=""><figcaption></figcaption></figure>

可以看到是这个base64解码一下啊

<figure><img src="../.gitbook/assets/image (71).png" alt=""><figcaption></figcaption></figure>





### 5.根据容恨寒的安卓手机分析，收到的刷单.rar的MD5值是\[答案：202cb962ac59075b964b07152d234b70]\[★★☆☆☆] 1 dc52d8225fd328c592841cb1c3cd1761&#x20;

去压缩包里面去看文件名是这个的

```
dc52d8225fd328c592841cb1c3cd1761
```

<figure><img src="../.gitbook/assets/image (72).png" alt=""><figcaption></figcaption></figure>

导出

<figure><img src="../.gitbook/assets/image (73).png" alt=""><figcaption></figcaption></figure>

放到hash my files

<figure><img src="../.gitbook/assets/image (74).png" alt=""><figcaption></figcaption></figure>







### 6.根据容恨寒的安卓手机分析，收到的刷单.rar的解压密码是\[答案：abcdg@1234@hd]\[★★★☆☆] 2 wlzhg@3903@xn&#x20;

既然是potato里面的，应该密码也在这个里面，去数据库里看看。把他们个人的对话，特别是别人发给他的对话，看一下，每一行base64解码。可以用一个网站。[https://www.base64decode.org/zh/](https://www.base64decode.org/zh/)

```
wlzhg@3903@xn
```



<figure><img src="../.gitbook/assets/image (75).png" alt=""><figcaption></figcaption></figure>

上面说密码电话说了。然后就是密码规则。

<figure><img src="../.gitbook/assets/image (76).png" alt=""><figcaption></figcaption></figure>

就是中间的四位是随机组合，所以我们可以爆破密码。

我这里先写一个字典，用python写一个字典，然后用字典来爆破。

```python
str1 = "wlzhg@"
str2 = "@xn"

for i in range(10000):
    strx = "{:04d}".format(i)
    str = str1+strx+str2
    print(str)
```

<figure><img src="../.gitbook/assets/image (77).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (78).png" alt=""><figcaption></figcaption></figure>





### 7.根据容恨寒的安卓手机分析，发送刷单.rar的用户的手机号是\[答案：15137321234]\[★★★★☆] 2 15137326185&#x20;

其实从对话中我们也能看出来，应该是德严慧发给他的，我们直接去找她的电话号码就行

```
15137326185
```

<figure><img src="../.gitbook/assets/image (79).png" alt=""><figcaption></figcaption></figure>

在$o的表里面的login是电话

<figure><img src="../.gitbook/assets/image (80).png" alt=""><figcaption></figcaption></figure>



### 8.根据容恨寒的安卓手机分析，发送多个报表的用户来自哪个部门\[答案：理财部]\[★★★★★] 3 技术部&#x20;

群聊消息有一句你们都看看报表什么的，应该就是这个。然后这些文件在私聊中可以看到是臧发送给他的，所以问的应该是臧在哪个部门，把id对应起来就可以了。

```
技术部
```

<figure><img src="../.gitbook/assets/image (83).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (84).png" alt=""><figcaption></figcaption></figure>

臧的id是229，partenid是109

<figure><img src="../.gitbook/assets/image (85).png" alt=""><figcaption></figcaption></figure>

109的对应的是技术部

<figure><img src="../.gitbook/assets/image (86).png" alt=""><figcaption></figcaption></figure>





### 9.根据容恨寒的安卓手机分析，MAC的开机密码是\[答案：asdcz]\[★☆☆☆☆] 1 apple&#x20;

就在备忘录里面

```
apple
```

<figure><img src="../.gitbook/assets/image (81).png" alt=""><figcaption></figcaption></figure>









### 10.根据容恨寒的安卓手机分析，苹果手机的备份密码前4位是\[答案：1234]\[★☆☆☆☆] 1 1976&#x20;

备份密码也在备忘录

```
1976
```

<figure><img src="../.gitbook/assets/image (82).png" alt=""><figcaption></figcaption></figure>









### 11.根据魏文茵苹果手机分析，IMEI号是？\[答案格式:239471000325479]\[★☆☆☆☆] 1 358360063200634&#x20;

能跑出来的都不是事

```
358360063200634
```

<figure><img src="../.gitbook/assets/image (92).png" alt=""><figcaption></figcaption></figure>





### 12.根据魏文茵苹果手机分析，可能使用过的电话号码不包括？\[答案格式:13527821339]\[★☆☆☆☆] 1 4 18043618705 19212175391 19212159177 18200532661&#x20;

从他的账号挖掘里面的电话号码看出来是第四个不是

```
4
```

<figure><img src="../.gitbook/assets/image (93).png" alt=""><figcaption></figcaption></figure>



### 13.根据臧觅风的安卓手机分析，微信ID是\[答案：wxid\_av7b3jbaaht123]\[★☆☆☆☆] 1 wxid\_kr7b3jbooht322&#x20;

直接跑出来的

```
wxid_kr7b3jbooht322
```

<figure><img src="../.gitbook/assets/image (87).png" alt=""><figcaption></figcaption></figure>







### 14.根据臧觅风的安卓手机分析，在哪里使用过交友软件\[答案：杭州]\[★★★☆☆] 2 西安&#x20;

```
中国西安未央
```

<figure><img src="../.gitbook/assets/image (88).png" alt=""><figcaption></figcaption></figure>









### 15.根据臧觅风的安卓手机分析，嫌疑人从哪个用户购买的源码，请给出出售源码方的账号\[答案：1234524229]\[★☆☆☆☆] 1 5768224669&#x20;

一猜就在ins，中国管的这么严，直接平台就给你b了。

```
5768224669
```

<figure><img src="../.gitbook/assets/image (89).png" alt=""><figcaption></figcaption></figure>







### 16.根据臧觅风的安卓手机分析，购买源码花了多少BTC？\[答案：1.21]\[★☆☆☆☆] 1 0.08&#x20;

哈，0.08一口价

```
0.08
```

<figure><img src="../.gitbook/assets/image (90).png" alt=""><figcaption></figcaption></figure>



### 17.根据臧觅风的安卓手机分析，接收源码的邮箱是\[答案：asdasd666@hotmail.com]\[★☆☆☆☆] 1 molihuacha007@hotmail.com&#x20;

```
molihuacha007@hotmail.com
```



<figure><img src="../.gitbook/assets/image (91).png" alt=""><figcaption></figcaption></figure>



### 18.嫌疑人容恨寒苹果手机的IMEI是?\[答案格式:2000-01-01]\[★★☆☆☆] 1 353271073008914&#x20;

```
353271073008914
```

这个苹果手机要从mac里面导出备份。

<figure><img src="../.gitbook/assets/image (242).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (243).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (41).png" alt=""><figcaption></figcaption></figure>











### 19.嫌疑人容恨寒苹果手机最后备份时间是?\[答案格式:2000-01-01]\[★★☆☆☆] 1 2023-4-12 21:20:59&#x20;

```
2023-04-12 21:20:59
```



<figure><img src="../.gitbook/assets/image (42).png" alt=""><figcaption></figcaption></figure>







### 20.嫌疑人容恨寒苹果手机“易信”的唯一标识符（UUID）？\[答案格式:2000-01-01]\[★★★★☆]

易信是一个软件，难怪没有被取出来。uuid这种信息一般在plist里面

```
00A6A0C7-AD52-4FC2-9064-6D7BE58DBCE6
```



<figure><img src="../.gitbook/assets/image (43).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (44).png" alt=""><figcaption></figcaption></figure>







### 21.嫌疑人容恨寒苹果手机微信ID是?\[答案格式:2000-01-01]\[★☆☆☆☆]1 04:52:C7:FD:2C:64

```
```

ID没取出来，看来要自己取

<figure><img src="../.gitbook/assets/image (45).png" alt=""><figcaption></figcaption></figure>

emmm，答案这个真的不知道怎么找出来的。

网上答案都是认定是内部ID







***

## 计算机取证

### 1.嫌疑人魏文茵计算机的操作系统版本?\[答案格式:Windows 7 Ultimate 8603]\[★☆☆☆☆] 1 Windows 10 Pro 14393&#x20;

其实是都有的，但是要知道是操作系统，版本号，系统名称，build版本号都要写。

```
Windows 10 pro 14393
```

<figure><img src="../.gitbook/assets/image (56).png" alt=""><figcaption></figcaption></figure>



### 2.嫌疑人魏文茵计算机默认的浏览器是?\[答案格式:Internet Explorer]\[★☆☆☆☆] 1 3 Edge Internet Explorer Google Chrome 360浏览器&#x20;

```
3 谷歌
```

<figure><img src="../.gitbook/assets/image (57).png" alt=""><figcaption></figcaption></figure>





### 3.嫌疑人魏文茵计算机中以下那个文档不是嫌疑人最近打开过的文档?\[答案格式:D]\[★☆☆☆☆] 1 1 掠夺攻略.docx 工资表.xlsx 刷单秘籍.docx 脚本.docx&#x20;

最近访问的office里面有

```
1 掠夺攻略
```

<figure><img src="../.gitbook/assets/image (58).png" alt=""><figcaption></figcaption></figure>





### 4.嫌疑人魏文茵计算机中存在几个加密分区?\[答案格式:3个]\[★★☆☆☆] 1 1个&#x20;

在取证的时候就说了有bitlocker加密了第五个分区

```
1
```

<figure><img src="../.gitbook/assets/image (55).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (59).png" alt=""><figcaption></figcaption></figure>





### 5.嫌疑人魏文茵计算机中安装了哪个第三方加密容器?\[答案格式:VeraCrypt]]\[★☆☆☆☆] 1 TrueCrypt&#x20;

看到了TrueCrypt

```
TrueCrypt
```

<figure><img src="../.gitbook/assets/image (60).png" alt=""><figcaption></figcaption></figure>





### 6.接上题，嫌疑人魏文茵计算机中加密容器加密后的容器文件路径？\[答案格式:C:\xxx\xxx]\[★★☆☆☆] 1 C:\Users\WH\Documents&#x20;

因为先做了后面再来看的前面，发现是文件一般是txt，doc，等这种文件，大的可怕的，一般就是容器，而且可以先通过美亚排出来加密的文件，再来看。

```
分区2_本地磁盘[D]:\Users\WH\Documents\《穿越六十年代小知青》作者：平淡生活.txt

```

后面知道这种题用美亚跑，因为美亚的可以出一个疑似什么什么文件。

<figure><img src="../.gitbook/assets/image (187).png" alt=""><figcaption></figcaption></figure>





### 7.嫌疑人魏文茵计算机中磁盘分区BitLocker加密恢复秘钥为?\[答案格式: 000000-000000-000000-000000-000000-000000-000000-000000]]\[★★★☆☆] 2 000649-583407-395868-441210-589776-038698-479083-651618&#x20;

如果要找到这个，得用卷影分析

```
000649-583407-395868-441210-589776-038698-479083-651618 
```

对D盘卷影分析

<figure><img src="../.gitbook/assets/image (192).png" alt=""><figcaption></figcaption></figure>



这个提取密钥的方法需要用到软件，并且是第一次知道这么做，所以这个题要注意。过程在小工具介绍里面有详细的。

<div>

<figure><img src="../.gitbook/assets/屏幕截图 2024-05-07 232047.png" alt=""><figcaption></figcaption></figure>

 

<figure><img src="../.gitbook/assets/屏幕截图 2024-05-07 232217.png" alt=""><figcaption></figcaption></figure>

 

<figure><img src="../.gitbook/assets/屏幕截图 2024-05-07 232345.png" alt=""><figcaption></figcaption></figure>

</div>

<figure><img src="../.gitbook/assets/image (191).png" alt=""><figcaption></figcaption></figure>

然后直接挂载他，因为被破了。

<figure><img src="../.gitbook/assets/image (193).png" alt=""><figcaption></figcaption></figure>

然后看到有h盘

<figure><img src="../.gitbook/assets/image (194).png" alt=""><figcaption></figcaption></figure>

图片一有

<figure><img src="../.gitbook/assets/image (196).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (197).png" alt=""><figcaption></figcaption></figure>





### 8.嫌疑人魏文茵计算机中BitLocker加密分区中“攻略.docx”文档里涉及多少种诈骗方式?\[答案格式:11]\[★☆☆☆☆] 1 38&#x20;

输入我们上个找到的bitlocker密码之后，然后再跑一次自动取证。

```
38
```

<figure><img src="../.gitbook/assets/image (199).png" alt=""><figcaption></figcaption></figure>



<figure><img src="../.gitbook/assets/image (200).png" alt=""><figcaption></figcaption></figure>





### 9.投资理财团伙“华中组”目前诈骗收益大约多少?\[答案格式:10万]\[★★☆☆☆] 1 100万&#x20;

这个网上说是在微信聊天记录当中，有一个赚了100万，用密码破解出来，密钥也是从mem里面得到的。











### 9.通过对嫌疑人魏文茵计算机内存分析，print.exe的PID是？\[答案格式:123]\[★★☆☆☆] 1 728&#x20;

```
728
```

<figure><img src="../.gitbook/assets/image (176).png" alt=""><figcaption></figcaption></figure>



<figure><img src="../.gitbook/assets/image (175).png" alt=""><figcaption></figcaption></figure>







### 10.根据臧觅风的计算机分析，请给出技术人员计算机“zang.E01”的SHA-1?\[答案格式:7B2DC1741AE00D7776F64064CDA321037563A769]\[★☆☆☆☆] 1 239F39E353358584691790DDA5FF49BAA07CFDBB&#x20;

```
239F39E353358584691790DDA5FF49BAA07CFDBB
```

<figure><img src="../.gitbook/assets/image (50).png" alt=""><figcaption></figcaption></figure>







### 11.根据臧觅风的计算机分析，请给出该技术人员计算机“zang.E01”的总扇区数？\[答案格式:100,000,000]\[★★☆☆☆] 1 536,870,912&#x20;

开始以为火眼不能看，后来发现火眼的分区详情里面有，但是得算最后一个，开始加结束。

```
536,870,912
```

<figure><img src="../.gitbook/assets/image (172).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (173).png" alt=""><figcaption></figcaption></figure>





### 12.根据臧觅风的计算机分析，以下那个文件不是技术人员通过浏览器下载的？\[答案格式:A]\[★☆☆☆☆] 1 4 WeChatSetup.exe aDrive.exe Potato\_Desktop2.37.zip BaiduNetdisk\_7.27.0.5.exe&#x20;

```
4
```

<figure><img src="../.gitbook/assets/image (174).png" alt=""><figcaption></figcaption></figure>











### 13.根据臧觅风的计算机分析，请给出该技术人员邮件附件“好东西.zip”解压密码？\[答案格式:abc123]\[★★★★★] 3 molihuacha007&#x20;

臧密封买了一个源码密码是对方的邮箱，这个不知道有没有关系

```
kangshifu0008@gmail.com
```

<figure><img src="../.gitbook/assets/image (177).png" alt=""><figcaption></figcaption></figure>

### 14.根据臧觅风的计算机分析，该技术人员电脑内曾通过远程管理工具连接过服务器“master.k8s.com”,请给出连接的端口号？\[答案格式:22]\[★★☆☆☆] 1 2282&#x20;

```
2282
```

<figure><img src="../.gitbook/assets/image (54).png" alt=""><figcaption></figcaption></figure>







### 15.根据臧觅风的计算机分析，接上题，请给出服务器的密码？\[答案格式:password\[★★★★☆] 2 P@ssw0rd&#x20;

```
P@ssw0rd
```

这个没做出来不怪我自己，得先上网搜一搜才知道。made。[https://www.cnblogs.com/NoId/p/16754669.html](https://www.cnblogs.com/NoId/p/16754669.html)

<figure><img src="../.gitbook/assets/image (49).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (48).png" alt=""><figcaption></figcaption></figure>

需要对这个解密。网上的解密脚本我们直接用工具。

<figure><img src="../.gitbook/assets/image (181).png" alt=""><figcaption></figcaption></figure>







### 16.根据臧觅风的计算机分析，据该技术人员交代，其电脑内有个保存各种密码的txt文件，请找出该文件，计算其MD5值？\[答案格 式:7B2DC1741AE00D7776F64064CDA321037563A769]\[★★★★★] 3 C6E19349E4695FB734314BB10E891245&#x20;

这道题，我找到的文件和题目答案给的文件的md5不一样，但是那个文件名就是passwords.txt的文件，

```
C1934045C3348EA1BA618279AAC38C67
```

<figure><img src="../.gitbook/assets/image (182).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (183).png" alt=""><figcaption></figcaption></figure>





### 17.根据臧觅风的计算机分析，该技术人员曾使用过加密容器反取证技术，请给出该容器挂载的盘符？\[答案格式:A]\[★☆☆☆☆] 1 F&#x20;

```
F
```



<figure><img src="../.gitbook/assets/image (51).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (52).png" alt=""><figcaption></figcaption></figure>



### 18.根据臧觅风的计算机分析，请给出该技术人员电脑内keePass的Master Password？\[答案格式:password12#]\[★★★★☆] 2 xiaozang123!@#&#x20;

找到了一个txt文件里面写了这个，但是他也没有特意说这个master password就是密码就是这个。所以这个地方。我觉得是自己漏了什么关键信息。而且后面看到下载了kee pass这个软件，但是没有看到，说明被truecrypt做成镜像里面了。这里找镜像文件我一直觉得很难，因为有时候他的后缀是txt和word，然后我觉得是从他们的大小，一般大的不正常，就猜测是truecrypt加密文件。

<figure><img src="../.gitbook/assets/image (184).png" alt=""><figcaption></figcaption></figure>

同样的方法来提取

<figure><img src="../.gitbook/assets/image (201).png" alt=""><figcaption></figcaption></figure>

别人的都能提取出来，我的一直提取不出来，不知道为什么，用passware kit了，反正是一样的，服了。

<figure><img src="../.gitbook/assets/image (209).png" alt=""><figcaption></figcaption></figure>

还是没有，我都怀疑是不是我的资料和他们的不是一个。算了，无语了。但是在我看文件的时候，生成了资料unprotected.docx文件





### 19.根据臧觅风的计算机分析，请给出该技术人员所使用的爬虫工具名称？\[答案格式:xxx]\[★★☆☆☆] 1 后羿采集器&#x20;

```
后羿采集器
```

<figure><img src="../.gitbook/assets/image (53).png" alt=""><figcaption></figcaption></figure>



### 20.根据臧觅风的计算机分析，接上题，该技术人员通过该采集器一共采集了多少条人员信息数据？\[答案格式:10,000]\[★★★★★] 3 19,225&#x20;

害，开始以为是从我们解密的文件夹里面的，后来发现不是，是从手机上面看到的聊天记录有臧发了很多文件，哪个文件才是采集器采集到的文件，所以我们从potato的文件夹里面去找。并且是德发送给了容，所以我们要去容的手机的potato的attach里面去找。

```
19225
```

<figure><img src="../.gitbook/assets/image (210).png" alt=""><figcaption></figcaption></figure>

一个一个算就行，

100+18+18970+96+29+12(其实最后一个我数出来是13，但答案写的12）

<figure><img src="../.gitbook/assets/image (211).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (212).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (213).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (214).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (215).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (216).png" alt=""><figcaption></figcaption></figure>



### 21.根据臧觅风的计算机分析，以下那个不是该技术人员通过爬虫工具采集的数据？\[答案格式:A]\[★☆☆☆☆] 1 3 中国证券投资基金业 协人员信息 仓山区市场监 督管理局行政 执法人员信息 清平镇卫生院基本公共卫生 服务 仓山区市场监督管理局行政执 法人员信息&#x20;

很明显是马头镇

```
3
```

文件名就是

<figure><img src="../.gitbook/assets/image (220).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (221).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (222).png" alt=""><figcaption></figcaption></figure>









### 22.根据臧觅风的计算机分析，该嫌疑人曾浏览过“阿里云WebDAV”，请给出该“阿里云WebDAV”端口号？\[答案格式:2211]\[★★☆☆☆] 1 8080&#x20;

```
8080
```

<figure><img src="../.gitbook/assets/image (198).png" alt=""><figcaption></figcaption></figure>

所以这个是一个云盘，我们在google的记录里面看到的有阿里云云盘

我们去google记录里可以看到192.168.8.2下面的就是阿里云云盘，所以端口是8080

<figure><img src="../.gitbook/assets/image (202).png" alt=""><figcaption></figcaption></figure>





### 23.根据臧觅风的计算机分析，请给出该技术人员电脑内代理软件所使用的端口号？\[答案格式:2211]\[★★☆☆☆] 1 7890&#x20;

代理软件是clash for windows，自己也用过，所以直接去仿真去看就行。

```
7890
```

<figure><img src="../.gitbook/assets/image (224).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (225).png" alt=""><figcaption></figcaption></figure>





### 24.根据臧觅风的计算机分析，接上题，请给出该代理软件内订阅链接的token？\[答案格式:abc1234df334…]\[★★☆☆☆] 1 d4029286acc8bfd97818d5f8724f0f0a&#x20;

这个题如果用过会好做很多，因为做过我自己偶时候也会出现这个界面，看到token。

```
d4029286acc8bfd97818d5f8724f0f0a 
```

<figure><img src="../.gitbook/assets/image (226).png" alt=""><figcaption></figcaption></figure>













### 25.根据臧觅风的计算机分析，请给出该技术人员电脑内用于内部通联工具的地址和端口？\[答案格式:www.baidu.com:1122]\[★★★☆☆] 2 im.pgscup.com:6661&#x20;

内部通信软件我们从前面就知道是potato了，直接打开仿真看看就行。

```
im.pgscup.com:6661
```

<figure><img src="../.gitbook/assets/image (223).png" alt=""><figcaption></figcaption></figure>









### 26.根据臧觅风的计算机分析，请给出该电脑内存镜像创建的时间（北京时间）？\[答案格式:2023-05-06 14:00:00]\[★☆☆☆☆] 1 2023-04-27 17:57:53&#x20;

内存镜像的时间查看，可以用imageinfo这个指令。volatility去看看。是这个systemtime是我们需要的时间，也就是创建时间。

```
2023-04-27 09:57:53
```

<figure><img src="../.gitbook/assets/image (208).png" alt=""><figcaption></figcaption></figure>



### 27.根据臧觅风的计算机分析，以下那个不是“chrone.exe”的动态链接库？\[答案格式:A]\[★★★★☆] 2 2 ntdll.dll iertutil.dll wow64cpu.dll wow64win.dll&#x20;

虽然可以用工具，但是跑一下时间花的太久了，直接用指令。可以看到只有第二个没有看到。

```
2
```

<figure><img src="../.gitbook/assets/image (227).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (228).png" alt=""><figcaption></figcaption></figure>





### 28.根据臧觅风的计算机分析，请给出“\REGISTRY\MACHINE\SYSTEM”在内存镜像中的虚拟地址是多少？\[答案格式:0xxxxx123…]\[★★☆☆☆] 1 0xffffab861963e000&#x20;

这个可以上网先搜搜虚拟地址在哪里看。后面看到说在注册表里面

```
0xab861963e000
```

<figure><img src="../.gitbook/assets/image (229).png" alt=""><figcaption></figcaption></figure>













### 29.根据臧觅风的计算机分析，据嫌疑人交代，其电脑上曾存打开过一个名为“账号信息.docx”的文档，请给出该文档的最后访问时间（北京时间）？\[答案格 式:2023-05-06 14:00:00]\[★★★★☆] 2 2023-04-27 17:55:32&#x20;

直接找到这个文件，注意有两个，要区分以下，是否有x，并且最后的访问时间。

```
2023-04-27 17:55:32

```

<figure><img src="../.gitbook/assets/image (203).png" alt=""><figcaption></figcaption></figure>





### 30.根据臧觅风的计算机分析，接上题，请给出该文档的存储路径？\[答案格式:C:\xxx\xxx]\[★★★☆☆] 2 D:\ backup\mydata 

这个注意就是美亚取出来的盘的顺序名字不一样，所以其实虽然我软件显示E，其实是D。

<pre><code><strong>D:\backup\mydata\账号信息.docx
</strong>
</code></pre>

<figure><img src="../.gitbook/assets/image (204).png" alt=""><figcaption></figcaption></figure>





### 31.嫌疑人容恨寒苹果电脑的系统版本名称是？\[答案格式:注意大小写]\[★☆☆☆☆] 1 Monterey&#x20;

注意这里是系统版本的名称，不是版本，版本能跑出来是12.6，但是名称得上维基百科去搜最新的

```
Monterey
```

<figure><img src="../.gitbook/assets/image (206).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (205).png" alt=""><figcaption></figcaption></figure>



### 32.嫌疑人容恨寒苹果电脑操作系统安装日期是？\[答案格式:2000-01-01]\[★★☆☆☆] 1 2022-10-9&#x20;

```
2022-10-9
```

<figure><img src="../.gitbook/assets/image (207).png" alt=""><figcaption></figcaption></figure>





### 33.嫌疑人容恨寒苹果电脑的内核版本是？\[答案格式:xxxxx 11.0.4，注意大小写]\[★☆☆☆☆] 1 Darwin 21.6.0&#x20;

内核版本用指令uname，并且苹果系统就是unix，所以也可以用这个指令，但是要仿真一下。

```
Darwin 21.6.0 
```

<figure><img src="../.gitbook/assets/image (231).png" alt=""><figcaption></figcaption></figure>



### 34.嫌疑人容恨寒苹果电脑有多少正在运行的后台程序？\[答案格式:20]\[★★☆☆☆] 1 1&#x20;

ps指令，这些学linux的嘶吼学过

```
1
```

<figure><img src="../.gitbook/assets/image (232).png" alt=""><figcaption></figcaption></figure>



### 35.嫌疑人容恨寒苹果电脑最后一次关机时间（GMT）？\[答案格式:2000-01-01 01:00:09]\[★★☆☆☆] 1 2023-04-14 07:55:50&#x20;

```
2023-04-14 15:55:50
```

<figure><img src="../.gitbook/assets/image (230).png" alt=""><figcaption></figcaption></figure>



### 36.嫌疑人容恨寒苹果电脑执行过多少次查询主机名称命令？\[答案格式:20]\[★★★☆☆] 2 13&#x20;

其实这里要注意一下，他执行了history -c，就是清楚了很多指令，所以单纯用history找出来的，肯定少了很多。这里只算hostname这一个口令，hostnamectl只要是在仿真电脑上试过就知道用不了。而且我们是看.zsh\_history,之前只知道bash\_history，现在知道了.zsh\_history也是，而且其实看到.bash\_history被清理了。但是取证软件取出来了，这个地方有迷惑性，就是网上的答案，各有个样，就是没有标准答案的一样的解。但是我大概知道标准答案怎么出来的。

```
13
```

<figure><img src="../.gitbook/assets/image (233).png" alt=""><figcaption></figcaption></figure>

是在会话框一栏搜索的hostname，就是13个

<figure><img src="../.gitbook/assets/image (234).png" alt=""><figcaption></figcaption></figure>





### 37.从嫌疑人容恨寒苹果电脑中找出“陆文杰”提现金额是？\[答案格式:20]\[★★★★☆] 2 10&#x20;

其实这个文件在我仿真的时候就看到了在桌面上，但是当时苦于打不开，后来看wp知道是看16进制发现其实是一个rar文件，考了两个misc了。

```
10
```

<figure><img src="../.gitbook/assets/image (235).png" alt=""><figcaption></figcaption></figure>

改个后缀

<figure><img src="../.gitbook/assets/image (236).png" alt=""><figcaption></figcaption></figure>

需要密码才能打开，这个密码还是他们的命名规则，害，还是得前后文连接。后缀需要改为hn了，因为是hn区。

字典爆破

<figure><img src="../.gitbook/assets/image (237).png" alt=""><figcaption></figcaption></figure>

要仔细看字段对应的，有一个最新金额。



<figure><img src="../.gitbook/assets/image (238).png" alt=""><figcaption></figcaption></figure>

最新是10.1，但是估计要整数才能提款，就是10





### 38.从嫌疑人容恨寒苹果电脑中找出嫌疑人容恨寒上午上班时长是？\[答案格式:8小时]\[★★★★☆] 2 2.5小时&#x20;

就在脚本里面。从9：00-12：00，比我轻松。

```
2.5
```

<figure><img src="../.gitbook/assets/image (239).png" alt=""><figcaption></figcaption></figure>





### 39.从嫌疑人容恨寒苹果电脑中找出“万便”的邮箱是？\[答案格式:xxx@xxx.xx]\[★★★★☆] 2 IxCnq3@yDp.net&#x20;

还是揭秘出来的里面的人员信息，直接搜

```
IxCnq3@yDp.net
```

<figure><img src="../.gitbook/assets/image (240).png" alt=""><figcaption></figcaption></figure>





### 40.通过分析得出嫌疑人容恨寒小孩的年龄是？\[答案格式:10岁]\[★★★☆☆] 2 6岁&#x20;

这道题很迷惑，因为他的垃圾篓里面就是8年级的，所以很容易认为是8年级的孩子的奥数题，后面仔细看是1年纪学习手册，emmmm， 好卷啊，我沉默了。

```
6
```

<figure><img src="../.gitbook/assets/image (241).png" alt=""><figcaption></figcaption></figure>





***

## 二进制文件分析



### 1.根据魏文茵的计算机分析，恶意程序加了什么类型的壳\[答案：asdcz]\[★★☆☆☆]UPX

开始以为是大蚂蚁，后来上网搜发现不是

<figure><img src="../.gitbook/assets/image (46).png" alt=""><figcaption></figcaption></figure>

除此之外，还有个print.exe运行了，但是我们不认识。应该就是这个

<figure><img src="../.gitbook/assets/image (47).png" alt=""><figcaption></figcaption></figure>

导不出来是为什么，妈的。酸了，我也不做二进制，后面再来填这个坑。



### &#x20;2.根据魏文茵的计算机分析，恶意程序调用了几个dll\[答案：1]\[★★★☆☆] 5











### 3.根据魏文茵的计算机分析，恶意程序中send函数被多少个函数调用\[答案：1]\[★★★☆☆] 6







### 4.根据魏文茵的计算机分析，恶意程序远控端ip\[答案：120.1.2.3]\[★★☆☆☆] 192.168.8.110





### 5.根据魏文茵的计算机分析，恶意程序远控端端口\[答案：123]\[★★☆☆☆] 6069









### 6.根据魏文茵的计算机分析，恶意程序用到是tcp还是udp\[★★★☆☆]  1 tcp  udp







### 7.根据魏文茵的计算机分析，恶意程序能执行几条命令\[答案：123]\[★★★★☆] 5&#x20;







### 8.根据魏文茵的计算机分析，恶意程序加密电脑文件对应是哪个命令\[答案：1a]\[★★★☆☆]  6s







### 9.根据魏文茵的计算机分析，恶意程序加密哪些后缀文件\[★★★☆☆] 1,2,3,4 docx xlsx pdf doc







### 10.根据魏文茵的计算机分析，编写该程序电脑的用户名是\[答案：12345]\[★★★★★]  22383









### 11.嫌疑人魏文茵计算机中“工资表.xlsx”中，发放工资总金额为：\[答案格式:12345]]\[★★★★★] 44300



















***

## 暗网取证

### 1.臧觅风电脑使用暗网浏览器版本是？\[答案格式：10.0.0]\[★☆☆☆☆] 12.0.4  &#x20;

之前为了了解暗网，特意下载过这个软件，但是没进去用过，用的是洋葱浏览器才可以访问一些暗网网页。并且要开代理才能用。











### 2.臧觅风电脑使用的暗网浏览器历史记录中最多浏览内容是？\[答案格式：制作]\[★★☆☆☆] BT币















### 3.臧觅风电脑使用的暗网网浏览器书签“社工库”添加的时间是？\[答案格式：2000-01-0101:00:09]\[★★★★☆] 2022-05-2721:49:33

















### 4。臧觅风电脑使用的暗网浏览器第一次使用时间是？\[答案格式：2000-01-0101:00:09]\[★★★☆☆] 2022-05-2721:20:19













### 5.臧觅风电脑使用的暗网浏览器扩展应用中“ftp.js”文件的md5值是？\[答案格式：字母小写]\[★★★★★]ea86403d1de3089b3d32fe5706d552f6















***

## 物联取证

### 1.请给出该软路由管理的IP地址？\[答案格式:192.168.1.1]\[★☆☆☆☆] 192.168.8.20&#x20;

&#x20;   查看/etc/config/network文件，可以看到配置的lan，就是ip地址。

```
192.168.8.20
```

<figure><img src="../.gitbook/assets/image (244).png" alt=""><figcaption></figcaption></figure>



### 2.请给出该软路由管理员的密码？\[答案格式:admin123!@#]\[★★★☆☆] P@ssw0rd

密码需要去/etc/shadow去看。

```
P@ssw0rd
```

<figure><img src="../.gitbook/assets/image (245).png" alt=""><figcaption></figcaption></figure>

或者之前题目要从SECURECRT里面找到了服务器的密码，直接用就行.

### 3.请给出阿里云WebDAV的token？\[答案格式:bac123sasdew3212…]\[★★☆☆☆] afc455bdc29a45b18f3bae5048971e76

```
afc455bdc29a45b18f3bae5048971e76
```

这里也是搭建好网站啊，就是要先配置网络，害这个网络真的有点难配置。找了很久才发现这个方式配置成功，首先在仿真的时候就应该选择net模式，用火眼仿真可以自己配置。

仿真好后修改/etc/config/network文件的proto，把协议的static（静态）修改位dhcp。并且记下这个掩码。

<figure><img src="../.gitbook/assets/image (32).png" alt=""><figcaption></figcaption></figure>

把这个掩码修改为虚拟机的net网卡的网关。比如本人的是

<figure><img src="../.gitbook/assets/image (34).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/屏幕截图 2024-05-09 132531.png" alt=""><figcaption></figcaption></figure>

然后reboot重启。

<figure><img src="../.gitbook/assets/image (35).png" alt=""><figcaption></figcaption></figure>

然后可以看到分配的ip是192.168.29.132

然后在主机上输入ip

账号密码都知道了，前面有

<figure><img src="../.gitbook/assets/image (39).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/屏幕截图 2024-05-09 133147.png" alt=""><figcaption></figcaption></figure>





### 4.请给出该软路由所用机场订阅的token？\[答案格式:bac123sasdew3212…]\[★★☆☆☆]502f6affe3c7deb071d65fb43effc06d

机场就是我们常说的vpn，这里有两个，一个是小猫咪，clash for windows一个是小火箭，开始只看小猫咪去了，忘了还有小火箭。

```
502f6affe3c7deb071d65fb43effc06d
```

<figure><img src="../.gitbook/assets/屏幕截图 2024-05-09 191405.png" alt=""><figcaption></figcaption></figure>



### 5.请给出该软路由数据卷的UUID？\[答案格式:8adn28hd-00c0c0c0…]\[★★☆☆☆]9a89a5ec-dae6-488a-84bf-80a67388ff37&#x20;

uuid，上网查也可以知道指令blkid可以看，注意是数据卷的，会有data的类型说明的。

```
9a89a5ec-dae6-488a-84bf-80a67388ff37 
```

<figure><img src="../.gitbook/assets/屏幕截图 2024-05-09 191449.png" alt=""><figcaption></figcaption></figure>









### 6.请给出该软路由的共享路径？\[答案格式:/home/data]\[★★☆☆☆]/mnt/data

取服务-》网络共享下面去找

```
/mnt/data
```

<figure><img src="../.gitbook/assets/image (38).png" alt=""><figcaption></figcaption></figure>







***

## 服务器取证

### 1.请给出IM服务器的当前Build版本？\[答案格式:11111]\[★☆☆☆☆] 17763   &#x20;

这里首先要从上一题的物联网取证中提取出来服务器取证的镜像，emmm，真的，正常人谁能想得到，我真服了。并且这个文件路径是在/mnt/data/IM，还挺直接的，应该用find找找的，但是想不到在这个里面。

害，然后本来想用xshell去传送文件，但是又60G，emmm，然后看wp知道rclone，这种传输大容量的文件很快，不然60G用xshell，很慢。

<figure><img src="../.gitbook/assets/屏幕截图 2024-05-09 192750.png" alt=""><figcaption></figcaption></figure>



```
```













### 2.请给出IM聊天服务的启动密码？\[答案格式:3w.Baidu.com]\[★★★★★] 123w.pgscup.com









### 3.请给出该聊天服务器所用的PHP版本？\[答案格式:7.2.5]\[★★★★☆] 7.4.32









### 4.请给出该服务器所用的数据库类型及版本？\[答案格式:mysql5.7.1]\[★★★★★]  MariaDB10.4.12







### 5.请给出该服务器MySQL数据库root账号的密码？\[答案格式:3w.baidu.com]\[★★★★★] www.upsoft01.com









### 6.请给该IM服务器内当前企业所使用的数据库？\[答案格式:admin\_admin]\[★★★★☆]  antdbms\_usdtreclub









### 7.请给出该组织“usdtreclub”内共有多少个部门（不含分区）？\[答案格式:1]\[★★★☆☆] 6









### 8.客户端消息传输采用哪种加密形式？\[答案格式:A]\[★★☆☆☆] 2 AES128 AES256 DES Base64









### 9.以下那个不是此系统提供的应用？\[答案格式:A]\[★★☆☆☆] 4 云盘 审批 会议 考勤











### 10.请给出“2023-04-1121:48:14”登录成功此系统的用户设备MAC地址？\[答案格式:08-AA-33-DF-1A]\[★★★☆☆]80-B6-55-EF-90-8E







### 11.请给出用户“卢正文”的手机号码？\[答案格式:13888888888]\[★★★★☆]13580912153



















***

## 集群服务器取证

### 1.请给出集群master节点的内核版本？\[答案格式:2.6.0-104.e11.x86\_64]\[★☆☆☆☆] 3.10.0-957.el7.x86\_64    &#x20;











### 2.请给出该集群的pod网络？\[答案格式:192.168.0.0/24]\[★★★★☆] 10.244.0.0/16







### 3.请给出该集群所用的网络插件？\[答案格式:abcd]\[★★☆☆☆] calico











### 4.默认ns除外，本集群共有多少个ns？\[答案格式:1]\[★★★☆☆] 8







### 5.请给出该集群的集群IP？\[答案格式:192.168.0.0]\[★★☆☆☆] 10.96.0.1











### 6.请给出该ns为“licai”svc为“php-svc”的访问类型？\[答案格式:Abc]\[★★☆☆☆] NodePort    &#x20;











### 7.请给出ns为“shuadan”下的的PHP版本？\[答案格式:1.1]\[★★★★★] 7.2











### 8.请给出本机集群所使用的私有仓库地址？\[答案格式:192.168.0.0]\[★★★★☆]  192.168.8.20













### 9.接上题，请给出登录该私有仓库所用的token？\[答案格式:bae213ionada21…]\[★★★★★] dXNlcjozVy5wZ3NjdXAuY29t











### 10.请给出“licaisite”持久化存储的大小？\[答案格式:10G]\[★★☆☆☆] 6G

















### 11.接上题，请给出对应的存储持久化声明名称？\[答案格式:abc-abc]\[★★★☆☆] licaisite-pvc



















### 12.请给出集群内部署网站所使用数据库的IP地址和端口号？\[答案格式:192.168.0.0:8080]\[★★★☆☆] 61.150.31.142:3306   &#x20;









### 13.请给出网站“vip.kefu.com”所使用的端口号？\[答案格式:8080]\[★★☆☆☆] 8083

















### 14.请给出网站“vip.shuadan.com”连接数据库所使用的账号和密码？\[答案格式root/password]\[★★★★★] vip.shuadan.com/nFRrSNh6Msnbtpay









### 15.请给出调证数据库的版本号？\[答案格式5.7.1]\[★★★★★]  5.6.50













### 16.请给出刷单网站客服域名？\[答案格式:http://www.baidu.com:8080/login.html]\[★★★★★]  http://vip.kefu.com:8083/admin/login/index/business\_id/1.html







### 17.请给出理财客服系统用户“admin”共有多少个会话窗口？\[答案格式:123]\[★★★★★] 8











### 18.刷单客服是嵌套在刷单源码下那个文件内，请给出该文件在网站源码内的目录和文件名？\[答案格式:www.baidu.com:8080/login.html]\[★★★★★]vip.shuadan.com/application/index/view/user/user.html











### 19.请统计出刷单网站后台累计提现成功的金额？\[答案格式:1000]\[★☆☆☆☆]  7611  &#x20;











### 20.请给出受害人上级的电话号码？\[答案格式:13888888888]\[★★★☆☆] 18727164573









### 21.请给出刷单网站受害人加款的时间（北京时间）？\[答案格式:2023-05-0614:00:00]\[★★★☆☆] 2023-04-1214:57:32











### 22.该理财网站曾经被挂马，请给出上传木马者的IP？\[答案格式:192.168.10.10]\[★★★☆☆] 103.177.44.10&#x20;





### 23.接上题，请找到此木马，计算该木马的md5？\[答案格式:123dadgadad332...]\[★★★☆☆] 339c925222a41011ac1a7e55ec408202&#x20;













### 24.请统计该投资理财平台累计交易额为多少亿？\[答案格式:1.8]\[★★☆☆☆] 1.42











### 25.请给出该虚拟币投资平台内用户“李国斌”的银行卡号？\[答案格式:622222222222222]\[★★★☆☆]  6212260808001710173&#x20;











### 26.分析该虚拟币投资平台财务明细表，用户“13912345678”共支出多少钱（cnc）,结果保留两位小数？\[答案格式:10000.00]\[★★★★★]24817.99



















































































































































































































