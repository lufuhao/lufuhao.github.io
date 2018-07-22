title: Latest PICARD-tools installation (from v1.124)
link: https://lufuhao.wordpress.com/2014/11/14/latest-picard-tools-installation-from-v1-124/
author: lufuhao
description: 
post_id: 1366
created: 2014/11/14 20:59:28
created_gmt: 2014/11/14 11:59:28
comment_status: open
post_name: latest-picard-tools-installation-from-v1-124
status: publish
post_type: post

# Latest PICARD-tools installation (from v1.124)

PICARD Homepage

> <http://broadinstitute.github.io/picard/>
> 
> <https://github.com/broadinstitute/picard>

Here I am not going to  introduce how excellent and useful this toolset is, but to celebrate the the author finally integrate all tools into one package. So you will not need to find the package name every time you want it. Actually it’s boring to do that: set PICARDHOME or PICARD_HOME to the package root directory and find a package you want, and java –jar PACKAGE_NAME [options] ….

Now I am happy to to see all the functions are integrated into one package ‘picard.jar’. so you would just call 

$> java –jar PICARDHOME/picard.jar

Here I am giving my way to install PICARDtools and use it simply.

 

**Installation (Linux):**

 

**1\. create a directory you want to install PICARDtools**

$> mkdir -p $HOME/programs/picard/v1.124/x86_64

$> cd $HOME/programs/picard/v1.124/x86_64

 

**2\. Download the software from github**

$> wget <https://github.com/broadinstitute/picard/releases/download/1.124/picard-tools-1.124.zip>

$> unzip picard-tools-1.124.zip

$> ls

picard-tools-1.124

$> mv picard-tools-1.124 bin

$> cd bin

$>ls -1

htsjdk-1.124.jar  
libIntelDeflater.so  
picard.jar  
picard-lib.jar

 

3\. [optional] create one link to directly call picard.jar

$> vim picard

#press **i** on your keyboard to enter VIM edit mode

#pasta following into terminal:

\-------------------------------file border---do not copy this line-------------------------------

#!/bin/sh

CurDir=$(cd `dirname $(readlink -f $0)`; pwd)

java -jar $CurDir/picard.jar "$@"

\------------------------------file border-----do not copy this line----------------------------- 

#press **Esc**, and then input **:wq** to save and exit 

#This is to create one file containing content described above. Same with other text editor, like gedit 

$> chmod +x ./picard

#And then put this picard file into you PATH by editing ~/.bashrc, /etc/profile or other ways. 

$> export PATH=$HOME/programs/picard/v1.124/x86_64/bin:$PATH

in my case, to make the setting immediately work. But remember to change the picardpath to yours. 

**** 

**4\. test**

$> picard

USAGE: PicardCommandLine <program name> [-h