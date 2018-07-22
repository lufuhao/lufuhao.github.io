title: Run a cluster job with graphical interface
link: https://lufuhao.wordpress.com/2013/11/27/run-a-cluster-job-with-graphical-interface/
author: lufuhao
description: 
post_id: 1273
created: 2013/11/27 21:52:15
created_gmt: 2013/11/27 12:52:15
comment_status: open
post_name: run-a-cluster-job-with-graphical-interface
status: publish
post_type: post

# Run a cluster job with graphical interface

Recently I need to run some jobs but with graphical interface. In short, you need a X-server under Windows if you have not  got any. Or you may need to ass the –X behind ssh, like “ssh –X host”

 

1\. Windows: 

source from <http://www.zw1840.com/blog/zw1840/2008/10/putty-xming-linux-gui.html>

1.1 install Xming

download Xming and Xming-fonts from <http://sourceforge.net/projects/xming/>

![Xming.install.03](http://lufuhao.files.wordpress.com/2013/11/xming-install-03_thumb.png)

![Xming.install.05](http://lufuhao.files.wordpress.com/2013/11/xming-install-05_thumb.png)

After the install finished, run XLaunch to configure Xming X server. Good to use the default setting

![Xming.config.01](http://lufuhao.files.wordpress.com/2013/11/xming-config-01_thumb.png)

Display 代表一套 I/O 设备，包括显示、鼠标、键盘；Display Number 就是这套 I/O 设备的代号；同时 Display Number 还决定了 Xming X server 的 TCP 端口，端口号为 6000 + Display Number。Linux 主机上的应用程序通过此端口建立与 Xming X server 的连接。

***important: Remember this DISPLAY NUMBER, and later we will use that.**

![Xming.config.02](http://lufuhao.files.wordpress.com/2013/11/xming-config-02_thumb.png)

![Xming.config.03](http://lufuhao.files.wordpress.com/2013/11/xming-config-03_thumb.png)

![Xming.config.04](http://lufuhao.files.wordpress.com/2013/11/xming-config-04_thumb.png)

Save the configuration into .xlaunch file. Double click this .xlaunch file would start the Xserver service. You may find the Xming icon on the task bar.

1.2. Config your Putty

![PuTTY.config.01](http://lufuhao.files.wordpress.com/2013/11/putty-config-01_thumb.png)

Fill the host you want to connect to. Connection type: ssh

![PuTTY.config.02](http://lufuhao.files.wordpress.com/2013/11/putty-config-02_thumb.png)

[Optional] Fill in your auto-login username. If not, it will promote the username when you try to connect.

![PuTTY.config.03](http://lufuhao.files.wordpress.com/2013/11/putty-config-03_thumb.png)

Check “Enable X11 forwarding”, and fill in the X display location with **localhost:Display_number**. the display number would be the number you setup in Xming as described above. By default, it should be “localhost:0”

![PuTTY.config.05](http://lufuhao.files.wordpress.com/2013/11/putty-config-05_thumb.png)

[Ignore this if you want to set up again each time when you connect to the host] You may save you Putty setting by going back to the session part. Input a name under the “Saved Sessions”and click save. Next time, click the saved setting, and then load. Enjoy…

 

 

2\. Linux 

Under Linux, you may need some parameter behind ssh to enable the X-server/Xorg-like display service when you ssh to the host. For me, under linux workstation (CentOS 6.4), just one simple command: “**ssh –X** host.address”. 

Hope this would be helpful.