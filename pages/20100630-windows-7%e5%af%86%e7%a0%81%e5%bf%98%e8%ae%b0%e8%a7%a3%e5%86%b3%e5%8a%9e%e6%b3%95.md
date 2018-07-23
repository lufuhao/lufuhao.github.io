title: Windows 7密码忘记解决办法
link: https://lufuhao.wordpress.com/2010/06/30/windows-7%e5%af%86%e7%a0%81%e5%bf%98%e8%ae%b0%e8%a7%a3%e5%86%b3%e5%8a%9e%e6%b3%95/
author: lufuhao
description: 
post_id: 97
created: 2010/06/30 12:51:52
created_gmt: 2010/06/30 12:51:52
comment_status: open
post_name: windows-7%e5%af%86%e7%a0%81%e5%bf%98%e8%ae%b0%e8%a7%a3%e5%86%b3%e5%8a%9e%e6%b3%95
status: publish
post_type: post

# Windows 7密码忘记解决办法

由于无法使用管理员帐号进入Windows 7，辅助工具比较大，已经回不到xp时代的pe一键删除密码了，不过用Windows 7的system账户运行cmd命令可以强制修改账户密码！就拿xp+Windows 7为例（没有安装双系统也可以进入pe）。 

**第一步：**

由于cmd在系统目录，文件更改首先要获得文件所有权。打开“D:＼windows＼system32”(假设Windows 7安装在D盘)，右击“arrator.exe”选择“权限”——高级——所有者，将当前xp下管理员帐号设置为所有者（如果没有当前帐号在列表，则单击 “其他账户”，手动输入当前账户名）。单击“确定”返回权限设置窗口，点击“添加”，将当前管理员帐户添加到列表，并将账户对该文件读取权限设置为“完全控制”。 

**第二步：**

操作同上，设置当前账户对“cmd.exe”权限为完全控制，然后将“narrator.exe”重命名为 “narrator1.exe”，“cmd.exe”重命名为“narrator.exe”。 

**第三步：**

（如果是以administrator账户登录的就不用这一步了）重启登录Windows 7，在登录界面单击右下角的“轻松访问”按钮，在打开的窗口勾选“启动讲述人”，此时启动的就是cmd窗口了（是以system身份开启的，自然有管理员权限啦～），在cmd输入下面的命令开启administrator账户，重启即可使用administrator了： 

net user administrator /active:yes (解释：强制开启administrator账户) 

net user administrator 123456/add （解释：强制将用户administrator密码改为123456） 

**第四步：**

既然administrator账户无法使用，那么就创建个呗，要和它一样的权限不就行了嘛；重启登录Windows 7，在登录界面单击右下角的“轻松访问”按钮，在打开的窗口勾选“启动讲述人”，启动cmd窗口，输入： 

net user admin 123 /add 回车； 

net localgroup administrators admin /add 回车； 

**第五步：**

重启，进入admin账户就可以了。