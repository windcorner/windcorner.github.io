---
layout: post
title: "动态库中的同名函数问题"
category: study
tags: [linux,C]
description: |
  本文主要说明一个事例编译选项“-Bsymbolic”的作用，在编译无命名空间的动态库时推荐使用，比如常见的C语言动态库。
---
{% include JB/setup %}

  最近一个客户的商用机重启后，突然出现一个奇怪的业务异常问题。业务进程A一启动，就出现大量的错误，尝试core掉进程发现堆栈类似下面的情况：

       3#   ...
       4#   funcC  (at /opt/oracle/D.so
       5#   MODA::funB  (at /home/modA/XXXX)
  funC明明是modA下的一个动态库中的函数，怎么会调到oracle下的一个动态库函数呢？
  通过nm发现原来两个库中都有funcC这个函数，由于加载的函数导致了这个问题。
   

  原来编译动态库时如果不加“-Bsymbolic”这个选项，在应用程序中（或加载在前的）的同名函数或全局变量会覆盖动态库中的函数或全局变量。

   解决问题就很简单了，重新编译一下funcC所在的库，再重启一下进程即可。

