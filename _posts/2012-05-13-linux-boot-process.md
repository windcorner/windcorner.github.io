---
layout: post
title: "linux启动过程"
category: research
tags: [linux,x86]
description: |
  本文主要说明x86系统从加电到内核启动的系统启动过程。
---
{% include JB/setup %}


###CPU加电
系统上电后，CPU初始化时会将寄存器CS置为0xFFFFFh,IP置为0x0000h,执行0xFFFF:0000h处的跳转指令执行BIOS程序。
###BIOS
BIOS,不同架构的系统BIOS程序加载的首地址稍有不同，但功能基本相似：

- 执行POST
- 在启动设备中搜寻boot loader
- 将boot loader stage1程序加载入内存并执行

简单地说，就是BIOS执行INT 0x19，加载MBR内容至0x7c00,然后跳转执行。

为啥是0x7c00位置呢？

0x7c00=32KB-1024B，是32K的最后一个KB,这个magic number不是intel决定的，所以我们在X86相关的文档中无法找到这个magic number的说明，这个magic number属于 BIOS specifiction 。这个0x7c00 是 IBM PC 5150 BIOS developer team 决定的。 

###MBR
一般情况下，系统从硬盘启动。硬盘中存放boot load stage1程序的扇区称为MBR(Master Boot Record)。

一般来说，它为硬盘的首个扇区，该扇区的512字节主要用于存放如下内容：

- boot loader stage1程序   446字节
- 硬盘分区表                 64字节
- 有效标记（魔术字）0x55AA     2字节

分区表中一个分区占用16字节，即一个硬盘当前只支持4个主分区。若为扩展分区，实际保存的即为第一个分区后的一个地址（存放逻辑分区表）。

###Stage1

stage1的功能较简单，主要是加载位于第二个扇区的start.S程序到0x7000，并拷贝到0x8000执行。常见的stage1程序就是grub了，如果用户在启动时可以看到GRUB Shell，那就是stage1的真正画面。

###Stage1.5
在/boot/grub目录存放着Stage1_5中可以加载的文件系统映像文件:

    #ll  /boot/grub/*1_5
    -rw-r--r-- 1 root root 7552 May 11 2010 /boot/grub/e2fs_stage1_5
    -rw-r--r-- 1 root root 7840 May 11 2010 /boot/grub/fat_stage1_5

e2fs _stage1 _5对应的即为ext2/etx3的文件系统。

不过，通常stage1.5阶段的文件不会放在目录中，因为当stage1还没加载stage1.5时，原则上是不能识别ext2的，当然也无法找到stage1.5这个文件，所以，它的作用是加载磁盘的第三个扇区到第N个扇区到内存，N取几，取决与文件系统的代码的大小。但是文件系统千千万，我们不可能把所有文件系统的功能文件放在磁盘的扇区里面，那怎么办呢？在grub安装的时候，能够识别启动设备的文件系统，比如是ext3文件系统，所以只需要将ext3部分的 e2fs_stage1 _5 放入扇区。
 


###Stage2
至此阶段，有了文件系统，就可以不用计算扇区，可以直接访问文件了。系统执行/boot/grub/stage2并寻找/boot/grub/menu.lst来选择系统内核并引导。
此后，就完成了grub的引导过程，加载linux内核，并进行内核的启动。