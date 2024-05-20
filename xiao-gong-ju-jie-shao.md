---
description: 主要是会用到的一些小脚本或者是工具
---

# 小工具介绍

## 1.查看SecureCRT

{% file src=".gitbook/assets/how-does-SecureCRT-encrypt-password-master.zip" %}

### （1）官方文档：

```
$ ./securecrt_cipher.py -h
usage: securecrt_cipher.py [-h] {enc,dec} ...

positional arguments:
  {enc,dec}
    enc       perform encrypt operation
    dec       perform decrypt operation

options:
  -h, --help  show this help message and exit
```

```
$ ./securecrt_cipher.py enc -h
usage: securecrt_cipher.py enc [-h] [-2] [--prefix {02,03}] [-p PASSPHRASE]
                               PASSWORD

positional arguments:
  PASSWORD              the plain password to encrypt

options:
  -h, --help            show this help message and exit
  -2, --v2              encrypt/decrypt with "Password V2" algorithm
  --prefix {02,03}      the prefix of encrypted passwords generated with
                        "Password V2" algorithm
  -p PASSPHRASE, --passphrase PASSPHRASE
                        the config passphrase that SecureCRT uses
```

```
$ ./securecrt_cipher.py dec -h
usage: securecrt_cipher.py dec [-h] [-2] [--prefix {02,03}] [-p PASSPHRASE]
                               PASSWORD

positional arguments:
  PASSWORD              the encrypted password to reveal

options:
  -h, --help            show this help message and exit
  -2, --v2              encrypt/decrypt with "Password V2" algorithm
  --prefix {02,03}      the prefix of encrypted passwords generated with
                        "Password V2" algorithm
  -p PASSPHRASE, --passphrase PASSPHRASE
                        the config passphrase that SecureCRT uses
```

<figure><img src=".gitbook/assets/image (178).png" alt=""><figcaption></figcaption></figure>

（2）使用例子：

这里我们用来解密试试

<figure><img src=".gitbook/assets/image (180).png" alt=""><figcaption></figcaption></figure>

记得要把u去掉

<figure><img src=".gitbook/assets/image (179).png" alt=""><figcaption></figcaption></figure>





***

## 2.EFDD

{% file src=".gitbook/assets/ElcomsoftForensicDiskDecryptor(jb51.net).rar" %}

## （1）官方文档

是一个加密磁盘破解工具，一般是从内存文件中提取密钥，一般电脑再带一个mem文件的，就有可能要用到这个。

（2）使用例子：

比如我们要解密一个truecrypt的一个容器密码，我们从他给的mem文件里面提取出来。

也就是说，我们是为了解密容器。

<figure><img src=".gitbook/assets/image (188).png" alt=""><figcaption></figcaption></figure>

<figure><img src=".gitbook/assets/image (189).png" alt=""><figcaption></figcaption></figure>

<figure><img src=".gitbook/assets/image (190).png" alt=""><figcaption></figcaption></figure>









***

## 3.volatility

放这个是为了更好的翻找指令。

```
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





***

## 4.john

## （1）官方文档。

[https://xz.aliyun.com/t/3958](https://xz.aliyun.com/t/3958)



### （2)使用

直接 john  ./shadow就行。

```
```









