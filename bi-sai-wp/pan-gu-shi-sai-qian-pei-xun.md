# 盘古石赛前培训

## 1 手机题目

### 1.通过通话记录分析，去重后，嫌疑人一共主动联系过多少个号码？（答题格式：11）（1分）

&#x20;很多记录，所以决定直接去数据库找，写一个select语句，各个字段的含义也在网上找到了。

```
71
```

<figure><img src="../.gitbook/assets/image (253).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (254).png" alt=""><figcaption></figcaption></figure>



&#x20;

&#x20;

### 2.接上题，主动联系的号码中，最为频繁的号码是？（答题格式：13800138000）（1分）

&#x20;

```
15185491986
```

<figure><img src="../.gitbook/assets/image (255).png" alt=""><figcaption></figcaption></figure>





### 3.接上题，上述号码一共主动联系了多少次？（答题格式：11）（1分）

&#x20;

```
65
```

<figure><img src="../.gitbook/assets/image (256).png" alt=""><figcaption></figcaption></figure>





### 4.分析通话记录中的主叫号码，在凌晨（0点到6点），嫌疑人联系最频繁的号码是？（答题格式：13800138000）（2分）

&#x20;

```
24
```

<figure><img src="../.gitbook/assets/image (258).png" alt=""><figcaption></figcaption></figure>





### 5.分析嫌疑人的所有通话记录（包括主被叫），号码归属地为江苏的一共有几个？（答题格式：11）（3分）

```
2
```

&#x20;有重复记得排除，忘记了重复，所以得到了15

<figure><img src="../.gitbook/assets/image (257).png" alt=""><figcaption></figcaption></figure>





### 6.分析手机中的聊天记录，嫌疑人曾经购买过加速服务，一共花了多少钱？（答题格式：12.34）（2分）

&#x20;聊天记录中，已经说的很明白了。

```
7500.00
```

<figure><img src="../.gitbook/assets/image (259).png" alt=""><figcaption></figcaption></figure>



### 7.该应用聊天记录中曾发送过一个压缩包附件，该文件的md5值是？（2分）

&#x20;一个是IP统计.ZIP，我们可以去包下面看看有没有attach，虽然但是在数据库里面，直接找到了他的md5，不需要我自己导出计算

```
84971a872b75dd6df55d3318bd10a5a2
```



<figure><img src="../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>

&#x20;





### 8.1) ？上述应用聊天记录中有删除记录，请找出删除记录在数据库中对应的msgId是？（3分）

删除的应该就是这一句但是我在数据库里面找不到这句话，后来我跳转源文件发现换了一个数据库。

后面挺听讲解的时候，老师在数据库也没有找出来，要用winhex去看数据库，真的第一次知道。我们用winhex去看4开头的数据库，emmmm。

```
```

&#x20;![](<../.gitbook/assets/image (13).png>)

<figure><img src="../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

这里有个问题，导出来的时候seq就少了一个











&#x20;

### 9.2) 嫌疑人有使用某款记账app，请问该app存储记账信息的数据库是？（答题格式：xxx.xxx）（2分）

解题思路：应用列表-包名-文件查看

&#x20;他有两款软件，都有记账功能。但是这个记账的数据库，好像在包里面没找到。上网搜了知道，后缀是so的是sqlite数据库，emmm。后面看到是在data/data下面是包的数据。。。。。。也没有卡看到，直接搜mymoney，然后看到了，记账记录，先试试的mymoney。

<figure><img src="../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>

挖财也有，就要看看有咩有使用记录了。

<figure><img src="../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

先看wacai，去看tradeinfo就是明细的表。发现有明细记录，就是这个。

<figure><img src="../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>

```
wacai365.so
```





### 10。记账app的所有记录中，用在打车上的费用合计是？（答题格式：12.34）（2分）

&#x20;看outgotype的表，开始以为是交通，后面仔细看有一栏是专门的打车。，然后去看money那个表。

<figure><img src="../.gitbook/assets/image (19).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

对typeid过滤1101，然后得到,但是其实是但是，但是我没有把他拉开，money好像不对。

<figure><img src="../.gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>

```
10122.50
```

&#x20;





### 11.3) 通过分析记账app，嫌疑人2023年12月14日，可能出现的城市是？（答题格式：北京）（1分）

解题思路：分析app数据库的备注信息comment字段

&#x20;在我看表的时候就看到了备注字段，

&#x20;只有两条，我来时间戳转换。

<figure><img src="../.gitbook/assets/image (22).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (23).png" alt=""><figcaption></figcaption></figure>

&#x20;

```
上海
```





### 12.4) 通过分析记账app，嫌疑人曾经租赁的服务器的月租费用是？（答题格式：12.34）（2分）

解题思路：分析app数据库，多表关联

&#x20;![](<../.gitbook/assets/image (24).png>)

<figure><img src="../.gitbook/assets/image (25).png" alt=""><figcaption></figcaption></figure>

```
99.00
```

&#x20;





### 13.5) 接上题，该服务器最后一次付费时间是？（答题格式：20240123）（1分）

&#x20;

```
20231101
```

&#x20;![](<../.gitbook/assets/image (26).png>)

&#x20;![](<../.gitbook/assets/image (27).png>)

&#x20;

&#x20;

&#x20;

### 14.6) 手机中安装了一款隐藏应用的app，请问该app的包名是？（答题格式：com.tencent.mm）（1分）

解题思路：根据应用列表，筛选User应用排查，亦可结合模拟器验证



名字就很明显。

&#x20;![](<../.gitbook/assets/image (28).png>)

```
com.app.hider.master.pro.cn
```







### 15.71) 该app隐藏了几个第三方应用？（答题格式：11）（2分）

&#x20;找到一个db数据库分析参数。害，没找到。





&#x20;

&#x20;

&#x20;





### 16.8) 该app设置了访问密码，请问访问密码是什么？（3分）

&#x20;xml的配置文件，包里面找。然后md5解码

```
```

&#x20;找到了一个apkkey，害，知道是找apk文件分析的xml文件，但是这个没有了就不知道了。

&#x20;







### 17.9) 嫌疑人微信中发送的关于公民信息的文件中，姓名为张圣宇的对象，其生日是？（答题格式：20230101）（2分）

info那个文件就是微信中发送的，但是这个人没有？？？？

好像是需要搜索info的文件，有几个不同的，都需要去找。

&#x20;











### 18.10) 嫌疑人微信数据库解密中用到的微信UIN是？（答题格式：123456或-123456）（1分）

&#x20;需要我们解密试试

<figure><img src="../.gitbook/assets/image (30).png" alt=""><figcaption></figcaption></figure>

&#x20;![](<../.gitbook/assets/image (31).png>)

&#x20;

```
wxid_2vlgmnpjs0u712
```



### 19.11) 嫌疑人微信发送的文件中，如果按照姓氏排名，出现次数最多的姓氏，一共出现了多少次？（答题格式：123）（3分）

我找错了一个文件。

```
8
```







***

## &#x20;计算机题目

&#x20;VC密码

<figure><img src="../.gitbook/assets/image (29).png" alt=""><figcaption></figcaption></figure>



### 1.12) 嫌疑人的电脑上创建了几个账户？（答题格式：11）（1分）

&#x20;有登录密码的才算自己创造的，也可以去c盘去看。

```
2
```

<figure><img src="../.gitbook/assets/image (34).png" alt=""><figcaption></figcaption></figure>





&#x20;

### 2.13) 嫌疑人电脑曾被远程连接过，控制方使用的IP地址为？（答案格式：192.168.1.1）（1分）

&#x20;除了这个都是127.0.0.1

```
192.168.230.1
```

<figure><img src="../.gitbook/assets/image (35).png" alt=""><figcaption></figcaption></figure>





&#x20;

### 3.嫌疑人使用的代理订阅URL为？（1分）

&#x20;

```
http://cloud.80567dbz.com/link/jmYrE3M3hc1bR7lx?sub=3
```

&#x20;![](<../.gitbook/assets/image (6).png>)

&#x20;

&#x20;



### 4.14) 嫌疑人使用的代理机场账号注册时间为(UTC+8)？（答题格式：2000-01-01 00:00:00）（2分）

解题思路：根据浏览器表单，直接登录嫌疑人的账号

&#x20;![](<../.gitbook/assets/image (5).png>)

&#x20;

&#x20;





### 5.15) 嫌疑人的电脑使用了存储池，复原类型为？（2分）

&#x20;

```
奇偶校验
```

&#x20;![](<../.gitbook/assets/image (7).png>)

&#x20;

### 6.16) 接上题该存储池为文件系统设置的簇大小为？（答题格式：8KB）（1分）

&#x20;发现在创建的时候直接就是默认的，那就说明是按照c盘或者是其他盘的簇大小。直接创建个文件查看属性就可以知道了。

```
4KB
```

&#x20;![](<../.gitbook/assets/image (8).png>)

&#x20;![](<../.gitbook/assets/image (9).png>)

c盘里面写一个字符，4kb就出来额。

<figure><img src="../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>





### 7.17) 嫌疑人计算机中的网站源码有木马，木马文件名为？（答题格式：xxx.xxx）（2分）

&#x20;

```
1234.php
```

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

这个看来是网站源码，

&#x20;![](<../.gitbook/assets/image (1).png>)





### 8.18) 嫌疑人电脑中联系人马天昊的电话号码是？（答题格式：13800138000）（3分）

&#x20;有一个



&#x20;







### 9.19) 嫌疑人曾通过ssh隧道连接过服务器数据库，该数据库对应密码为？（1分）

&#x20;

```
2394ksdffgk
```

&#x20;![](<../.gitbook/assets/image (4).png>)





### 10.20) 嫌疑人微软电子钱包中对应的银行卡号为？（答题格式：16位数字）（2分）

&#x20;需要用和浩晨的身份去登陆

知道是在微软的信息里面，需要去看。

&#x20;![](<../.gitbook/assets/image (3).png>)



```
```







### 21) 嫌疑人的服务器宝塔面板外网面板地址是？（2分）

&#x20;在云盘文件里面有一个txt文件

```
http://8.218.136.1:39709/bc13a679
```

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

&#x20;

&#x20;

22\) 嫌疑人曾通过图片作为载体隐藏信息，图片名称为？（答题格式：xxx.xxx）（2分）

&#x20;





&#x20;

23\) 嫌疑人电脑的即时通讯聊天记录曾被导出，导出了几组聊天记录（chats）？（答题格式：11）（3分）

&#x20;





&#x20;

24\) 嫌疑人曾购买网站源码，卖方用于收费的虚拟币地址为？（3分）

&#x20;

&#x20;

25\) 嫌疑人登录即时通讯工具用的本地锁定码（passcode）为？（3分）

&#x20;











***

## 3 服务器题目

&#x20;

镜像sdb.E01在系统中的挂载点是？（答题格式：/abc/abc）（1分）

&#x20;

&#x20;

26\) 网站域名的配置文件的绝对路径是？（答题格式：/abc/abc.abc）（2分）

&#x20;

&#x20;

27\) 分析网站，前台客服的eid值是？（答题格式：小写字母数字）（2分）

&#x20;

&#x20;

28\) 通过分析网站源码中网站后台的登录密码加密逻辑，给出密码654321加密后的密文是？（答题格式：小写字母数字）（3分）

&#x20;

29\) 分析后台菜单中的登录日志，出现最多的IP地址是？（答案格式：192.168.1.1）（2分）

&#x20;

&#x20;

30\) 结合后台和数据库分析，排除客服人员后，总投注金额从大到小，排在第三名的用户uid是？（答案格式：1234） （3分）

&#x20;

&#x20;

31\) 平台合计有8个总代（一级代理），请问在二级代理中，其代理下线人数（排除客服）是236的二级代理的id是？（答题格式：11）（3分）

&#x20;

&#x20;

32\) 接上题，统计每个二级代理的所有代理下线（排除客服）总投注金额排名（不考虑其他因素），排第8名的二级代理id是？（答题格式：11）（4分）

&#x20;

&#x20;





