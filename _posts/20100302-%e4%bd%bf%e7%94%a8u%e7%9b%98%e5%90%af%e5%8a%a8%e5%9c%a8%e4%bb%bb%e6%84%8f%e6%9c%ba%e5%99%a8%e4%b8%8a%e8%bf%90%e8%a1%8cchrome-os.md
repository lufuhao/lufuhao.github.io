title: 使用U盘启动在任意机器上运行Chrome OS
link: https://lufuhao.wordpress.com/2010/03/02/%e4%bd%bf%e7%94%a8u%e7%9b%98%e5%90%af%e5%8a%a8%e5%9c%a8%e4%bb%bb%e6%84%8f%e6%9c%ba%e5%99%a8%e4%b8%8a%e8%bf%90%e8%a1%8cchrome-os/
author: lufuhao
description: 
post_id: 119
created: 2010/03/02 06:50:27
created_gmt: 2010/03/02 06:50:27
comment_status: open
post_name: %e4%bd%bf%e7%94%a8u%e7%9b%98%e5%90%af%e5%8a%a8%e5%9c%a8%e4%bb%bb%e6%84%8f%e6%9c%ba%e5%99%a8%e4%b8%8a%e8%bf%90%e8%a1%8cchrome-os
status: publish
post_type: post

# 使用U盘启动在任意机器上运行Chrome OS

国外用户编译出可运行在任意电脑上的Chrome OS的USB启动镜像文件，并提供种子下载。这下可以摆脱虚拟机带来的不便了。不过，不要高兴太早，使用起来也不是那么舒服的。与[TualatriX编译的版本](http://imtx.cn/archives/1372.html)不同，下面这个方法得到的USB启动盘不限于上网本，任何机器都可以。TualatriX的版本因为需要运行在上网本上，条件限制所以我没有尝试。这个方法以及版均本来自国外，我还没下载，所以更没有试过，希望试过的在这里提供反馈。我也会尽快将它跑起来。 

**准备工作**： 

空U盘一个，4G就可以了，现在的U盘白菜价，因为Chrome OS的镜像文件大小是2,988,442,112字节，2G的U盘断然不行。支持USB启动的电脑一台，需要在BIOS里改为USB启动。准备一点儿运 气，如果你平时耗尽了人品，这次就要小心了，呵呵，因为不同机器上制作出来的千差万别，就像不同电脑装同样的Linux会产生完全不同的问题一样。需要下 载Chromium OS的文件，Google已经将其开源了。这里提供一个打包后的种子文件，通过BT下载吧 

<http://www.makeuseof.com/downloads/chromium_os_usb.torrent>

下载之后是个zip格式的系统磁盘镜像压缩文件，同时包含了一个用来制作Chrome OS的USB启动盘的小软件[Image Writer for Windows](https://launchpad.net/win32-image-writer)。 

**安装Chrome OS到USB驱动器**： 

解压下载的chrome_os_usb.zip文件，运行其中的Win32DiskImager.exe，如果遇到这个错误，忽略它，点OK即可，这是在寻找软盘，汗。 

![clip_image002](http://lufuhao.files.wordpress.com/2010/03/clip_image002_thumb.jpg?w=244)

程序运行后如下图所示，点击浏览选择刚才解压后出现的chrome_os.img文件。确保你已经插上U盘，这时候在磁盘下拉菜单里选择你的U盘的盘符。然后点击Write按钮，软件就开始将镜像写入U盘了。 

![clip_image004](https://s05mcq.blu.livefilestore.com/y1mcXlmf7w7MOeVxMczPi6tsmo8RMNEhoYGmooUEM6bkYk53hXr1L6Xep3jxzKXWiKkhrocGj-4BpIGjXdW_loez0gVEwEQvqZ95quwmO-8gz2JKH9SfIIXcrZuTvZJF5K8_vM-OEIgZxBKk63bpxZjrQ/clip_image004_thumb.jpg)

**启动Chromium OS**： 

镜像写完就算完成了，太方便了。重启电脑，如果已经修改为U盘启动的话，将会在10秒内出现chromium os的登陆界面了。本地用户名是**chronos**，密码是**password**。 

**Chromium OS****彩蛋**： 

这次又出彩了，当然的。主菜单（我们估计没法看见）里默认提供了三种邮件系统，分别是Gmail Hotmail和Yahoo! Mail。不过你要是点击Hotmail，结果连接到的还是Gmail，Yahoo! Mail连接到Yahoo的邮箱系统没错。看来，Google对Yahoo更友好一些… 

![clip_image006](https://s05mcq.blu.livefilestore.com/y1mU7kEI-Wa0w99ReoYROlefYcOiki2KK0dkJK1UYHKTeoPgGZVtPB9Kh-X1BnbNEwGX-KMNhpy0bjsbhy0nbW2wGh5h-4EcqiHSoxrmTZoOryRp1c7i9exzILQnkGkzcAfjZtaVqijICri9xPoi7gQ2g/clip_image006_thumb.jpg)