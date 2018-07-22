title: Blast2GO 本地化方法及注意事项
link: https://lufuhao.wordpress.com/2011/10/29/blast2go-%e6%9c%ac%e5%9c%b0%e5%8c%96%e6%96%b9%e6%b3%95%e5%8f%8a%e6%b3%a8%e6%84%8f%e4%ba%8b%e9%a1%b9/
author: lufuhao
description: 
post_id: 760
created: 2011/10/29 15:34:22
created_gmt: 2011/10/29 06:34:22
comment_status: open
post_name: blast2go-%e6%9c%ac%e5%9c%b0%e5%8c%96%e6%96%b9%e6%b3%95%e5%8f%8a%e6%b3%a8%e6%84%8f%e4%ba%8b%e9%a1%b9
status: publish
post_type: post

# Blast2GO 本地化方法及注意事项

#### 1\. 准备工作

? 下载Mysql数据库并安装：<http://www.mysql.com/downloads/mysql/> 。下个Essentials版本的就可以了。然后装上。（出问题自己解决） 

? 下载所需的数据文件： 

http://archive.geneontology.org/latest-full/go_201011-assocdb-data.gz (下载最新的) 

ftp://ftp.ncbi.nlm.nih.gov/gene/DATA/gene_info.gz 

ftp://ftp.ncbi.nlm.nih.gov/gene/DATA/gene2accession.gz 

ftp://ftp.pir.georgetown.edu/databases/idmapping/idmapping.tb.gz 

以上数据均下载最新的。 

? 下载local_b2g_db_tutorial_0609.zip. 在blast2go的网站上下载。 

#### 2\. 本地化构建

? 更改数据存放目录 

如果默认安装Mysql数据库的话，是装在C盘的，但是一般C盘的空间比较小，而要导入的数据很大，所以要改变一下Mysql 的数据存储目录。 

查看路径：mysql > show variables like “%dir%”; 在这个命令的结果中会看到datadir的路径，下边就是将这个路径改到别的位置。 

改变路径： 

停止mysql服务：net stop mysql; 更改my.ini中的datadir信息，并将原来的data目录copy到更改以后的路径中；重启服务：net start mysql. 

? 创建数据库和表 

在local_b2g_db_tutorial_0609 中有个b2g_db.sql文件，该文件是用来构建b2g数据库和建立相应表的文件，可以直接导入到mysql 中。 

原始的这个文件有几个错误，要改一下： 

1) 原始第9行：GRANT * , 改为 GRANT ALL. 

2) 原始第10行：添加 use b2g; 

3) 原始第26行：’description’ text NOT NULL default ‘’, 将default ‘’去掉。 

这样，这个文件就可以直接导入了。 

导入：sh> mysql –uroot –p < c:/b2g_db.sql 

这样在原来的mysql数据库中就多了一个b2g的数据库，同时这个库中还有三个表。自己查看一下，同时查看一下现在的数据存放目录是否改变了。 

? 导入数据： 

下边要导入已经下载好的4个数据文件。先都解压了，数据还是比较大的。 

1) 导入go_<YYYYMM>-assocdb-data数据(压缩包1.18G，解压后7.45G) 

进入mysql: 

sh> mysql b2g –s –b –uroot –p 

-s : silent mode: produce less out and speed up 

-b : suppress the beep when errors occur 

然后 mysql> source c:/go_****-assocdb-data 

时间很长，等吧。 

? 导入gene2accession 

mysql> load data local infile “path/gene2accession” into table gene2accession; 

OK, 无错误 

? 导入gene_info 

Mysql> load data local infile “path/geneinfo” into table gene_info; 

OK,无错误 

? 导入PIR file(idmapping) 

这个需要通过blast2go界面进行导入。Blast2go下的Tools-> DB configuration, 改变db-host, name, password，一般变为localhost, root , ***，然后选择 tools-> import PIR mapping to a local B2G-DB,导入。 

#### 3\. 总结

? 这里导入的数据仅仅解决了mapping的步骤，其他的步骤还需要通过网络，并没有本地化，mapping的速度是最慢的，本地化后会快很多。 

? 检测是否构建成功：在blast2go的主界面中点击绿色的箭头，出现图形说明数据库已经建好了。 

#### 4\. 可能出现的错误

? Network Connection Problem Premature EOF.过早结束。这个错误可能是由于杀毒软件造成的，关掉杀毒软件试试。不想关的话，放宽一下杀毒软件的过滤条件试试。 

? Blast2go的blast步骤需要多作几次，直到最后两次的miss blast一样为止，一般不存在blast结果的序列还是很少的。如果你没有大型的服务器，个人觉得通过NCBI blast反而比自己本地blast要快。 

? 富集分析：有时不报错，但是长时间不出结果，可能是杀毒软件的问题，关掉就很快出结果了。如果P值全为1，也这么做，试试看了。 

? Could not create the java virtual machine的问题，可能是启动的blast2go需要的内存太多，设定一个小的内存使用量就可以了。 

? Blast2go 会自动覆盖重复记录。会用后边的记录覆盖前边的记录。如果前面导入的结果为20个hit,后面相同记录为19个hit,那么最终的结果为19个hit.所以再比对nr和swissprot的时候，应该分开计算结果，然后再合并。 

? Blast2go导入本地blast结果文件，受到序列条目和文件大小的限制，3000条序列一个文件是可以的（测试过），占内存很严重。文件大小在100M左右是可以的。 

? 用独立的blast程序比对swissprot数据库出现问题，xml结果中hit-id不正确，导致blast2go无法识别，可能是formatdb时出现了错误，自己检查一下。 

? 一般GO 分类中，biological process的节点很多，在blast2go中，这步出图的时候总是容易卡死，需要改变一下blast2go配置文件中图形节点的最大值，改大点应该可以出来。 

#### 5\. 建议

? 富集分析做barchart的时候，用p-value比较好，可以在图形中显示over 和under。不推荐用FDR。 

? Blast2go出来的分类饼图是不包括unknown类别的，个人建议用blast2go出来的数据重新画一个分布饼图，将unknown类放进去。 

? 做blast的时候HSP的长度最好设定一下。 

可能碰到的问题：http://www.blast2go.org/tut 

Blast2GO 最新网址：<http://www.blast2go.com/b2ghome>，现在已经提供收费业务了，估计一点一点就会全部商业化了。个人建议还是学习人家的原理，如何mapping，如何打分，即使全部收费了也对我们的分析没多大影响，不能总被别人牵着鼻子走。 

[whybiocc原文链接](http://whybiocc.blog.163.com/blog/static/580358972010102231246886/)