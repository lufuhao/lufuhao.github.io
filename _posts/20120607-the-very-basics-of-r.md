title: The very basics of R
link: https://lufuhao.wordpress.com/2012/06/07/the-very-basics-of-r/
author: lufuhao
description: 
post_id: 1062
created: 2012/06/07 13:48:36
created_gmt: 2012/06/07 04:48:36
comment_status: open
post_name: the-very-basics-of-r
status: publish
post_type: post

# The very basics of R

> This page is designed to be a cheat sheet answering the most basic and fundamental questions that commonly come up when using R. Note that it is by no means intended to be an exhaustive list of the commonly used R functions. 

> **Q:  **What is a package?

A package is a collection or group of objects that R can use. A package may contain functions, data frames, or other objects, such as dynamically loaded libraries of compiled code.

> Q:  How do I see which packages I have available?

**library()**

> **Q:** How do I load a package?

**library("package_name")**

> **Q:** How do I see the documentation for a particular package?

**library(help="package_name")**

**help(package="package_name")**

> **Q:** How do I see the help file for a specific function?

**help("function_name") ?function_name**

> **Q:** How can I save my work?

You can save all the objects and functions that you have created in an **.RData** file, by using the **save** or the **save.image** functions. It is very important that you remember to include the **.RData** extension when indicating the file path because R will not supply it for you! 

**save(file="d:/file_name.RData")

save.image("d:/file_name.RData")**

On a PC you can also access this through the file menu: **File Save workspace** browse to the folder where you want to save the file and supply the file name of your choice 

> **Q:** How can I retrieve the work that I have saved using a **save.image** function?

The **load** function will load an **.RData** file. 

**load("d:/file_name.RData")**

On a PC you can also access this through the file menu: **File Load workspace** browse to the folder where you saved the **.RData** file and click open

> **Q:** How do I save all the commands that I have used in an R session?

You can save a history of your R session in an **.Rhistory** file by using the **history** function. It is very important that you remember to include the **.Rhistory** extension when indicating the file path because R will not supply it for you! 

**history("d:/file_name.Rhistory")**

On a PC you can also access this through the file menu: **File Save history** browse to the folder where you want to save the file and supply the file name of your choice

> **Q:** How can I retrieve the work that I have saved using a **history** function?

The **loadhistory** function will load an **.Rhistory** file. 

**loadhistory("d:/file_name.Rhistory")**

On a PC you can also access this through the file menu: **File Load history** browse to the folder where you saved the **.Rhistory** file and click open

> **Q:** How do I use a script of commands and functions saved in a text file?

**source("d:/file_name.txt")**

> **Q:** How do I get R to echo back the commands and functions in a script that I am sourcing into R? For example, if I have written functions and I want to see the functions being executed.

**source("d:/file_name.txt", echo=T)**

> **Q:** How do I close the help file when working on a Macintosh?

Typing **q** will close the help file and bring you back to the console.

> **Q:** How can I see a list of the objects that are currently available?

**objects() ls()**

> **Q:** How do I remove unwanted objects and functions?

**rm(object_name1, object_names2, etc.)**

**rm(function_name1, function_name2, etc.)**

> **Q:** What is the first thing to check if a function or object is behaving strangely and unexpectedly? 

Always check if there is a masked object or function which is being used instead of the object or function that you intended to use. If this is the case then the object or function can be removed by using the **rm** function as shown in the previous answer. 

**masked()**

**** 

[Souce link in UCLA academic technology Services](http://www.ats.ucla.edu/stat/r/faq/R_basics.htm)