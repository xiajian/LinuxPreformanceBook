# Linux Performance and Tuning Guidelines的中文翻译

首先，这本书的大多数翻译不是我翻译的(虽然还没翻译全)，其次，最初的想法将别人的网页上的翻译转换成markdown格式，最后，在尝试一下gitbook这个DRM-free的电子书生成工具。以下是一些介绍: 

> 备注： 以下均在Linux环境中操作。

## gitbook简介

gitbook是一个基于node的，用于构建图书使用的命令行工具。具体的怎么装node，推荐使用[NVM](https://github.com/creationix/nvm)。

以下是简要的安装命令如下: 

```
wget -qO- https://raw.githubusercontent.com/creationix/nvm/v0.24.0/install.sh | bash
# 或 
curl https://raw.githubusercontent.com/creationix/nvm/v0.24.0/install.sh | bash

nvm install 0.10
nvm use 0.10 
```

gitbook的安装和使用，可以参考 <http://gitbook-zh.wanqingwong.com/>。

使用的前置条件: 

* 一些Markdown语法，两个基本Markdown文件(README.md 和 SUMMARY.md)
* 常用的gitbook命令行: gitbook [serve|build|pdf|ebook|init]

## 实际操作

创建了一个`SUMMARY.md`，内容如下:

```
* [前言](preface.md)
* [第一章 了解Linux操作系统](chap1/README.md)
  - [1.1 Linux进程管理](chap1/Linux进程管理.md)
  - [1.2 Linux内存结构](chap1/Linux内存结构.md)
  - [1.3 Linux文件系统](chap1/Linux文件系统.md)
  - [1.4 硬盘I/O子系统](chap1/io子系统.md)
  - [1.5 网络子系统](chap1/network.md)
  - [1.6 了解Linux性能指标](chap1/indice.md)
* [第二章 监控和测量工具](chap2/README.md)
  - [2.1 介绍](chap2/intro.md)
  - [2.2 工具功能简介](chap2/工具功能简介.md)
  - [2.3 监控工具](chap2/mtool/README.md)
    - [2.3.1 top](chap2/mtool/top.md)
    - [2.3.2 vmstat](chap2/mtool/vmstat.md)
    - [2.3.3 uptime](chap2/mtool/uptime.md)
    - [2.3.4 ps与pstree](chap2/mtool/ps.md)
    - [2.3.5 free](chap2/mtool/free.md)
    - [2.3.6 iostat](chap2/mtool/iostat.md)
    - [2.3.7 sar](chap2/mtool/sar.md)
    - [2.3.8 mpstat](chap2/mtool/mpstat.md)
    - [2.3.9 numaster](chap2/mtool/numaster.md)
    - [2.3.10 pmap](chap2/mtool/pmap.md)
    - [2.3.11 netstat](chap2/mtool/netstat.md)
    - [2.3.12 iptraf](chap2/mtool/iptraf.md)
    - [2.3.13 tcpdump/ethereal](chap2/mtool/tcpdump.md)
    - [2.3.14 nmon](chap2/mtool/nmon.md)
    - [2.3.15 strace](chap2/mtool/strace.md)
    - [2.3.16 Proc文件系统](chap2/mtool/Proc文件系统.md)
    - [2.3.17 KDE System Guard](chap2/mtool/KDE System Guard.md)
    - [2.3.18 Gonme System Monitor](chap2/mtool/Gonme System Monitor.md)
    - [2.3.19 Capacity Manager](chap2/mtool/Capacity Manager.md)
  - [2.4 基准工具](chap2/btool/README.md)
    - [2.4.1 LMbench](chap2/btool/lmbench.md)
    - [2.4.2 IOzone](chap2/btool/iozone.md)
    - [2.4.3 netperf](chap2/btool/netperf.md)
    - [2.4.4 其它有用工具](chap2/btool/other.md)
* [第三章 分析性能瓶颈](chap3/README.md)
  - [3.1 确认瓶颈](chap3/确认瓶颈.md)
  - [3.2 CPU瓶颈](chap3/CPU瓶颈.md)
  - [3.3 内存瓶颈](chap3/内存瓶颈.md)
  - [3.4 硬盘瓶颈](chap3/硬盘瓶颈.md)
  - [3.5 网络瓶颈](chap3/网络瓶颈.md)
* [第四章 操作系统调优](chap4/README.md)
  - [4.1 调优原则](chap4/调优原则.md)
  - [4.2 安装注意事项](chap4/安装注意事项.md)
  - [4.3 更改内核参数](chap4/更改内核参数.md)
  - [4.4 处理器子系统调优](chap4/处理器子系统调优.md)
  - [4.5 虚拟内存子系统调优](chap4/虚拟内存子系统调优.md)
  - [4.6 硬盘子系统调优](chap4/硬盘子系统调优.md)
  - [4.7 网络子系统调优](chap4/网络子系统调优.md)
```

然后，运行`gitbook init`，创建如下的目录结构: 

```
▾ chap1/
    indice.md
    io子系统.md
    Linux内存结构.md
    Linux文件系统.md
    Linux进程管理.md
    network.md
    README.md
▾ chap2/
  ▾ btool/
      README.md
  ▾ mtool/
      README.md
    intro.md
    README.md
    工具功能简介.md
▾ chap3/
    CPU瓶颈.md
    README.md
    内存瓶颈.md
    硬盘瓶颈.md
    确认瓶颈.md
    网络瓶颈.md
▾ chap4/
    README.md
    处理器子系统调优.md
    安装注意事项.md
    更改内核参数.md
    硬盘子系统调优.md
    网络子系统调优.md
    虚拟内存子系统调优.md
    调优原则.md
  preface.md
```

从生成的目录结构可以猜出，gitbook大概不支持自动的三级目录的生成。

## 生成静态页面

gitbook自带的工具可以生成静态页面，运行命令为`gitbook serve .`(这里是在书籍的当前目录运行的)，输出如下： 

```
Press CTRL+C to quit ...

Live reload server started on port: 35729
Starting build ...
Successfully built!

Starting server ...
Serving book on http://localhost:4000
```

## 生成电子书

gitbook生成电子书，需要[Calibre](http://calibre-ebook.com)的支持，Calibre安装命令如下: 

```
sudo -v && wget -nv -O- https://raw.githubusercontent.com/kovidgoyal/calibre/master/setup/linux-installer.py | sudo python -c "import sys; main=lambda:sys.stderr.write('Download failed\n'); exec(sys.stdin.read()); main()"
```
> 注: 这里是个人环境为 64位ubuntu Linux，已安装了python。

生成pdf，还需要安装`gitbook-pdf`，命令如下: 

    npm install gitbook-pdf -g

生成epub，还需要安装`ebook-convert`，命令如下:
    
    npm install ebook-convert -g

至此，使用命令`gitbook [pdf|epub] .` 就能生成相应的电子书了。这样，个人自制电子书的工具也准备好了，这意味着，可以自制些电子书去忽悠别人了。
