---
description: 其实不想弄是因为就是指令的使用，但是蓝桥杯可能考这个，所以就试试看。
---

# 🔦 内存分析知识点

## 1.常用指令

主要的格式是

```
volatility -f [imame] --profile=[profile][plugin]
volatility -f [对象] --profile=[操作系统][插件参数]
```



### ①查看操作系统

在分析之前，先判断镜像信息，分析是哪个操作系统，使用imageinfo就可以。

```
volatility -f xxxx.vmem imageinfo
```



### ②获取正在运行的程序

pslit插件可以遍历内存镜像中的进程列表，显示每个进程的进程ID，名称，父进程ID，创建时间，退出时间，路径等信息。

```
volatility -f xxxx.vmem --profile=Win7SP1x64(或者其他的从imageinfo里面得到的） pslist
```



### ③提取正在运行的程序

procdump插件可以根据进程ID或者进程名称提取进程的内存映像，并保存为一个单独的文件，比如我要提取叫iexplore.exe程序,我们要知道他的pid进程号为2728，则

```
volatility -f xxx.vmem --profile=.... procdump -p 2728 -D ./
```

上面的D是提取程序后保存的地址。



### ④查看在终端里执行过的命令

cmdscan插件可以扫描内存镜像中的进程对象，提取已执行的cmd命令，将其显示在终端中

```
volatility -f xxx.vmem --profile=.... cmdscan
```



### ⑤查看进程在终端里运行的命令

cmdline插件可以用于提取进程执行命令行的参数和参数值

```
volatility -f xx.vmem --profile=... cmdline
```



### ⑥查找内存中的文件

filescan插件可以在内存中已经打开的文件句柄，从而获取文件名，路径，文件大小等信息，比如我们想找到hint.txt文件

```
volatility -f xx.vmem --profile=.. filescan | grep hint.txt
```

grep是linux下常用的命令之一，他在于用文件中查找指定的字符串，并将包含改字符串的行输出。

如果只是用filescan，不配合grep的话，volatility就会输出系统上的全部文件。



### ⑦提取内存中的文件

dumpfiles插件可以用来提取系统内存中的文件，比如我们要提取hint.txt文件，我们从上面的指令知道hint.txt内存位置谁0x000000011fd0ca70，我们可以用

```
volatility -f xx.vmem --profile=.. dumpfiles -Q 0x000000011fd0ca70 -D ./
```

Q是内存位置



### ⑧查看浏览器的历史记录

iehistory插件可以用于提取internet explore浏览器历史记录

```
volatility -f xx.vmem --profile=.. iehistory
```



### ⑨提取用户密码hash值并爆破

hashdump插件可以用于提取系统内存中的密码哈希值

```
volatility -f xx.vmem --profile=.. hashdump
```





### ⑩使用mimikatz提取密码

从windows操作系统中提取明文密码，哈希值以及其他安全凭据的工具

```
volatility -f xx.vmem --profile=.. mimikatz
```



### ⑩①查看剪切板里的内容

clipboard插件可以用于从内存转储中提取剪切板数据

```
volatility -f xx.vmem --profile=.. clipboard
```



### ⑩②查看正在运行的服务

svcscan用于扫描进程中所有的服务

```
svcscan
```





### ⑩③查看网络连接状态

netscan插件可以在内存转储中查找打开的网络连接和套接字，该命令将显示所有当前打开的网络连接和套接字，输出包括本地和远程地址，端口，进程ID和进程名称。

```
volatility -f xx.vmem --profile=... netscan
```



### ⑩④查看注册表信息

printkey是用于查看注册表的插件之一，他可以帮助分析人员查看和解析注册表中的键值，并提供有关键值的详细信息，如名称，数据类型，数据大小和值等

```
volatility -f xx.vmem --profile=... printkey
```

然后使用hivelist插件来确定注册表的地址

```
volatility -f xx.vmem --profile=... hivelist
```

查看注册表software表，

然后使用hivedump，可以提取windows注册表的内容，这里我们选择第一个来演示

```
volatility -f xx.vmem --profile=.... hivedump -o 0xfffff8a00127d010
```

o:hivelist列出的virtual值

根据名称查看具体子项的内容，这里以SAM\Domains\Account\Users\Names做演示，这个是Windows系统中存储本地用户账户信息的注册表路径，它包含了每个本地用户账户的名称和对应的SID信息

```
volatility -f xx.vmem --profile=... printkey -k "SAM\Domains\Account\Users\Names"
```

如果要提取整个全部的注册表，可以用dumpregistry

```
volatility -f xx.vmem --profile=... dumpregistery -D ./
```













## 参考门：

{% embed url="https://www.cnblogs.com/sakura--tears/p/17148293.html" %}

{% embed url="https://blog.51cto.com/baimao/6239392" %}













