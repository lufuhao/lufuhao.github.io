title: win7下实现全医药大辞典对Adobe Acrobat 9 pro. 取词
link: https://lufuhao.wordpress.com/2010/05/31/win7%e4%b8%8b%e5%ae%9e%e7%8e%b0%e5%85%a8%e5%8c%bb%e8%8d%af%e5%a4%a7%e8%be%9e%e5%85%b8%e5%af%b9adobe-acrobat-9-pro-%e5%8f%96%e8%af%8d/
author: lufuhao
description: 
post_id: 106
created: 2010/05/31 05:51:25
created_gmt: 2010/05/31 05:51:25
comment_status: open
post_name: win7%e4%b8%8b%e5%ae%9e%e7%8e%b0%e5%85%a8%e5%8c%bb%e8%8d%af%e5%a4%a7%e8%be%9e%e5%85%b8%e5%af%b9adobe-acrobat-9-pro-%e5%8f%96%e8%af%8d
status: publish
post_type: post

# win7下实现全医药大辞典对Adobe Acrobat 9 pro. 取词

解决办法：  
第一步： 首先找到词典的安装路径,例如默认安装路径, c:program fileskingyeemeddic 找到meddic 文件夹中的plugin文件夹打开,里面有三个文件：RwAcrob4c.api,RwAcrob5c.api,RwAcrob6c.api;   
如果是acrobat reader4.0就拷贝RwAcrob4c.api;   
如果是acrobat reader5.0就拷贝RwAcrob5c.api;   
如果是acrobat reader6.0就拷贝RwAcrob6c.api;   
如果是acrobat reader7.0，或7.0以上的版本，也拷贝RwAcrob6c.api;    
（win7下一般安装的是Adobe Acrobat 9 pro. ，其它低版本的可能不兼容）  
第二步： 找到Adobe Acrobat 9 pro. 的安装路径,打开plug_ins文件夹,然后将拷贝的文件粘贴进来。然后重新启动Adobe acrobat Pro软件。   
第三步： 此时一般就可以翻译pdf文件了。如果还是不行,就是Adobe acrobat Pro还需要设置一下。（很可能不行，那就看下步吧）  
第四步：在打开的Adobe acrobat PDF文档下，找到 编辑----首选项----在弹出的操作框中，找到选项 "一般"（位于左侧第四项）---------- 去掉 "仅适用认证的增效工具（U）"前面的勾。然后“确定”  
第五步：回退到Adobe acrobat PDF文档后，找到 编辑----首选项----在弹出的操作框中，找到选项 "页面显示"（位于左侧第三项）---------- 在右侧“页面布局（L）”中，选择 “单页”。然后“确定”