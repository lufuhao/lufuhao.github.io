title: Ubuntu 10.10+Win7 双系统重装 Win7 后恢复 Ubuntu 引导方法
link: https://lufuhao.wordpress.com/2011/03/05/ubuntu-10-10win7-%e5%8f%8c%e7%b3%bb%e7%bb%9f%e9%87%8d%e8%a3%85-win7-%e5%90%8e%e6%81%a2%e5%a4%8d-ubuntu-%e5%bc%95%e5%af%bc%e6%96%b9%e6%b3%95/
author: lufuhao
description: 
post_id: 525
created: 2011/03/05 15:20:41
created_gmt: 2011/03/05 06:20:41
comment_status: open
post_name: ubuntu-10-10win7-%e5%8f%8c%e7%b3%bb%e7%bb%9f%e9%87%8d%e8%a3%85-win7-%e5%90%8e%e6%81%a2%e5%a4%8d-ubuntu-%e5%bc%95%e5%af%bc%e6%96%b9%e6%b3%95
status: publish
post_type: post

# Ubuntu 10.10+Win7 双系统重装 Win7 后恢复 Ubuntu 引导方法

**起因:** 虽然一直在ubuntu下工作,但是前几天突然发现dreamweaver有wordpress的代码提示功能,让小狼心动不已,所以就打算在一直当成游戏机的win7上去搭建iis的php环境,鼓捣了一阵子后....悲剧地发现竟然无法打开was服务,说是找不到这个服务,百度,google了一阵，发现只有两个办法，尝试了一下都不成功，没办法.只能选择重装了,正好装个windows server 2008感觉感觉服务器版的windows有什么优点。   装完server 2008之后重启就更加悲剧地发现grub启动菜单不见了....不是重装了windows之后又要重装ubuntu吧....配置了好久的说,OMG!小狼决定说什么也不能重装ubuntu，就虚心地向google求救,经过一段时间的折腾,终于成功引导回ubuntu。现在就说说一下引导过程吧,注意了小狼用的是liveCD方法,就是装系统时用的光盘,没有的童鞋可以跳过了，当然想参考一下的也可以继续往下看。 **恢复引导方法：** 1.放进liveCD,重启,看到有界面出来的时候,选择试用,不要点安装。 2.进入ubuntu试用版后,打开终端,在左上角的应用程序->附件->终端那 3.输入以下命令: sudo fdisk -l   //得到的结果类似下面。查看ubuntu的根目录在那,这里没办法直接看出来,只能靠你自己识别,可以从分区的大小判断是不是根分区，就是在装ubuntu时，挂载点为 / 的那个分区 ![fdisk](http://www.aitilife.com/wp-content/uploads/2011/03/fdisk-300x127.png)   从图中的结果看出来，根分区在sda12.因为小狼记得分/分区的时候是分了20G的大小，并且当时是先分了/分区，然后再分了一个20G的/home分区的。所以判断出sda12是/分区，而不是sda13，虽然它也是20G.把sda12记住。 **注意：如果分区的时候，你单独把boot分区分出来了，还要多一步工作，就是找出boot分区:** 从上图可以看出,boot分区在sda8，因为它是最小的，只有200M.（你装ubuntu的时候分了多少就是多少） 记住sda8。 4.输入 

> sudo mount /dev/sda8 /mnt

因为小狼的单独把boot分区分出来了,并且它的位置在sda8.如果你没有单独把boot分区分出来.那就修改一下位置,改为 

> sudo mount /dev/你的/分区所在位置 /mnt

5.输入 

> sudo grub-install --root-directory=/mnt /dev/sda8

同样，如果你没有把boot分区单独分出来就改成 

> sudo grub-install --root-directory=/mnt /dev/你的/分区的位置

这里应该不会有什么问题，因为如果位置不对，无法安装，你可以一直输这个命令直到位置对了为止. 6.如果出现了no error report。那你就差不多成功了.然后sudo init 6.重启。 7.重启之后你会无奈地发现......windows也无法启动了，进入的是grub的命令行.....不要怕。进到这里你已经离成功不远了. 输入: root (hdX,Y）   //x为硬盘位置，如果你只有一快硬盘,X=0,如果有多块，相应设置x。Y为boot分区所在位置,这里是8.如果没有单独分boot分区,y就是你的/分区所在位置 linux /vmlinuz-2.xxxxx-generic root=/dev/sda12(无论你有没有把boot分区单独分出来,这里都要写/根分区的位置，否则无法完成启动,这里可以按tab完成填写) 如果没有单独把boot分区分出来，就是 

> linux /boot/vmlinuz-2.xxxxx-generic root=/dev/sda12 initrd /initrd.img-2.xxxxx-generic

或 

> initrd /boot/initrd.img-2.xxxxx-generic boot

到这里已经差不多完成了.因为你已经可以进入原来的ubuntu了，但是如果就这样不管了，那么下一次重启还需要重复一次上面的工作。这也太渗人了。。。 那最后就修复一下grub吧. 打开终端,输入 

> sudo update-grub

看到 

> Generating grub.cfg ... Found linux image: /boot/vmlinuz-2.6.35-27-generic Found initrd image: /boot/initrd.img-2.6.35-27-genericFound Windows Server 2008 (loader) on /dev/sda1 done

恭喜，现在已经全线完工了。赶快重启一下看看熟悉的grub引导菜单是不是回来了～ <http://wowubuntu.com/fix-grub.html>