---
description: 其实不想弄是因为就是指令的使用，但是蓝桥杯可能考这个，所以就试试看。
---

# 🔦 内存分析知识点

## 1.volatility2常用指令

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









***

## 2.volatility3

volatility3的用法和2不一样，不要指定 -profile，所以我们只要插件就行。



```sh
python3 vol.py [plugin] -f [image]
 
常用插件：
    layerwriter：列出内存镜像platform信息
    linux.bash：从内存中恢复bash命令历史记录
    linux.check_afinfo：验证网络协议的操作功能指针
    linux.check_syscall：检查系统调用表中的挂钩
    linux.elfs：列出所有进程的所有内存映射ELF文件
    linux.lsmod：列出加载的内核模块
    linux.lsof：列出所有进程的所有内存映射
    linux.malfind：列出可能包含注入代码的进程内存范围
    linux.proc：列出所有进程的所有内存映射
    linux.pslist：列出linux内存映像中存在的进程
    linux.pstree：列出进程树
    mac.bash：从内存中恢复bash命令历史记录
    mac.check_syscall：检查系统调用表中的挂钩
    mac.check_sysctl：检查sysctl处理程序的挂钩
    mac.check_trap_table：检查trap表中的挂钩
    mac.ifconfig：列出网卡信息
    mac.lsmod：列出加载的内核模块
    mac.lsof：列出所有进程的所有内存映射
    mac.malfind：列出可能包含注入代码的进程内存范围
    mac.netstat：列出所有进程的所有网络连接
    mac.psaux：恢复程序命令行参数
    mac.pslist：列出linux内存映像中存在的进程
    mac.pstree：列出进程树
    mac.tasks：列出Mac内存映像中存在的进程
    windows.info：显示正在分析的内存样本的OS和内核详细信息
    windows.callbacks：列出内核回调和通知例程
    windows.cmdline：列出进程命令行参数
    windows.dlldump：将进程内存范围DLL转储
    windows.dlllist：列出Windows内存映像中已加载的dll模块
    windows.driverirp：在Windows内存映像中列出驱动程序的IRP
    windows.driverscan：扫描Windows内存映像中存在的驱动程序
    windows.filescan：扫描Windows内存映像中存在的文件对象
    windows.handles：列出进程打开的句柄
    windows.malfind：列出可能包含注入代码的进程内存范围
    windows.moddump：转储内核模块
    windows.modscan：扫描Windows内存映像中存在的模块
    windows.mutantscan：扫描Windows内存映像中存在的互斥锁
    windows.pslist：列出Windows内存映像中存在的进程
    windows.psscan：扫描Windows内存映像中存在的进程
    windows.pstree：列出进程树
    windows.procdump：转储处理可执行映像
    windows.registry.certificates：列出注册表中存储的证书
    windows.registry.hivelist：列出内存映像中存在的注册表配置单元
    windows.registry.hivescan：扫描Windows内存映像中存在的注册表配置单元
    windows.registry.printkey：在配置单元或特定键值下列出注册表项
    windows.registry.userassist：打印用户助手注册表项和信息
    windows.ssdt：列出系统调用表
    windows.strings：读取字符串命令的输出，并指示每个字符串属于哪个进程
    windows.svcscan：扫描Windows服务
    windows.symlinkscan：扫描Windows内存映像中存在的链接
```



### ①查看映像信息

```
python .\vol.py -f xxx.raw windows.info
```

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

### ②查看映像进程

```
python .\vol.py -f xxx.raw windows.pslist
python .\vol.py -f xxx.raw windows.psscan
python .\vol.py -f xxx.raw windows.pstree
```

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

### ③**查看指定 pid 的进程**

```
python .\vol.py -f xxx.raw windows.pslist --pid 1234
```

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

### ④进程转储

```
python .\vol.py -o ./outputdir/ -f xxx.raw windows.pslist --pid 1234 --dump
```

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>



### ⑤查看句柄

<pre><code>python .\vol.py -f xxx.raw windows.handles
<strong>python .\vol.py -f xxx.raw windows.handles --pid 1234
</strong>
</code></pre>



### ⑥查看 DLL

```
python .\vol.py -f xxx.raw windows.dlllist
python .\vol.py -f xxx.raw windows.dlllist --pid 1234
```



### ⑦DLL 转储

```
python .\vol.py -o ./outputdir/ -f xxx.raw windows.dlllist --pid 1234 --dump

```



### ⑧查看命令行

```
python .\vol.py -f xxx.raw windows.cmdline
python .\vol.py -f xxx.raw windows.cmdline --pid 1234

```



### ⑨查看网络端口

```
python .\vol.py -f xxx.raw windows.netscan

```



### **⑩①查看完整的结果，但可能包含垃圾信息和虚假信息 (谨慎使用)**

```
python .\vol.py -f xxx.raw windows.netscan --include-corrupt

```



### ⑩②查看注册表信息

```
python .\vol.py -f xxx.raw windows.registry.hivescan
python .\vol.py -f xxx.raw windows.registry.hivelist

```



### ⑩③**查看指定过滤器 (文件夹) 下的注册表信息**

<pre><code><strong>python .\vol.py -f xxx.raw windows.registry.hivelist --filter FILTER
</strong></code></pre>



### ⑩④注册表信息转储

```
python .\vol.py -o ./outputdir/ -f xxx.raw windows.hivelist --filter FILTER --dump

```



### ⑩⑤查看注册表键值对

```
python .\vol.py -f xxx.raw windows.registry.printkey

```



### ⑩⑥**查看指定过滤器 (文件夹) 下的注册表信息，但需要 `hivelist` 提供的 `offset`**

```
python .\vol.py -f xxx.raw windows.registry.printkey --offset OFFSET

```



### ⑩⑦**查看指定键下的注册表值**

```
python .\vol.py -f xxx.raw windows.registry.printkey --key KEY

```



### ⑩⑧**打印所有键的信息**

```
python .\vol.py -f xxx.raw windows.registry.printkey --recurse
```



### ⑩⑨查看文件信息

```
python .\vol.py -f xxx.raw windows.filescan
```



建议通过 powershell 的 Select-String 或者 bash 的 grep 进行搜索，如：

```
python .\vol.py -f xxx.raw windows.filescan | grep "flag"

```



```
python .\vol.py -f xxx.raw windows.filescan | Select-String "flag"

```



### ②⑩文件转储

**需要 `pslist` 提供的 `pid`**

```
python .\vol.py -o ./outputdir/ -f xxx.raw windows.dumpfiles --pid 1234

```



**(推荐) 需要 `filescan` 提供的 `offset` (一般来说为 `physaddr`)**

```
python .\vol.py -o ./outputdir/ -f xxx.raw windows.dumpfiles --virtaddr 0xee1122
python .\vol.py -o ./outputdir/ -f xxx.raw windows.dumpfiles --physaddr 0xee1122

```



### ②①查找恶意注入代码

```
python .\vol.py -f xxx.raw windows.malfind
python .\vol.py -f xxx.raw windows.malfind --pid 1234

```



**恶意注入代码转储**

```
python .\vol.py -o ./outputdir/ -f xxx.raw windows.malfind --pid 1234 --dump

```









































## 参考门：

{% embed url="https://www.cnblogs.com/sakura--tears/p/17148293.html" %}

{% embed url="https://blog.51cto.com/baimao/6239392" %}

{% embed url="https://hasegawaazusa.github.io/vol3-note.html" %}















