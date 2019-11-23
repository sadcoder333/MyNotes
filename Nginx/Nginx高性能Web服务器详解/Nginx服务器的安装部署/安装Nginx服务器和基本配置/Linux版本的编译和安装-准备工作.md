# Linux版本的编译和安装-准备工作

Linux版本Nginx服务器的安装比Windows版要麻烦一些，需要先对Nginx源代码进行编译。在正式开始操作之前，我们先检查Nginx编译和安装需要的条件是否满足。

在安装Linux版本的Nginx服务器之前，首先需要安装一款Linux/UNIX操作系统发行版，常见的有Redhat、SUSE、Fedora、CentOS、Ubuntu、FreeBSD、Solaris以及Debian等。在一些Linux发行版和BSD的衍生版本中自带了Nginx软件的二进制文件，但由于Nginx软件升级频繁，这些编译好的二进制文件大都比较陈旧，建议使用者直接从较新的源代码编译安装。

本文以Fedora 16为例，介绍Nginx的安装与使用。Fedora Linux是比较具有知名度的Linux发行包之一，它基于Red Hat Linux。在Red Hat Linux终止发行后，由Fedora Project社区开发、Redhat公司赞助的Fedora Linux，用来取代Red Hat Linux在个人领域的应用。

Nginx服务器软件包（3.91 MB）和安装文件（4 MB左右）一共需要不到10 MB的磁盘空间，实际情况可能因为编译设置和第三方模块的加入有所不同。目前，在不加入第三方模块的条件下，应该保证10 MB以上的磁盘空间。

为了编译Nginx源代码，我们需要标准的GCC编译器。GCC的全称为GNU Compiler Collection，其由GNU开发，并以GPL及LGPL许可证发行，是自由的类UNIX及苹果电脑Mac OS X操作系统的标准编译器。因为GCC原本只能处理C语言，所以原名为GNU C语言编译器，后来得到快速扩展，可处理C++、Fortran、Pascal、Objective-C、Java以及Ada等其他语言。

除此之外，我们还需要Automake工具，以完成自动创建Makefile的工作。
由于Nginx的一些模块需要依赖其他第三方库，通常有pcre库（支持rewrite模块）、zlib库（支持gzip模块）和openssl库（支持ssl模块）等。
Fedora的安装光盘中包含了以上提到的软件和第三方库，如果在安装Fedora时选择了安装以上软件，则可以略过；如果没有，可以进行在线安装：
```
    yum –y install gcc gcc-c++ automake pcre pcre-devel zlib zlib-devel open openssl-devel
```
这里需要注意的是，我们不需要安装Autoconf工具。Nginx软件的自动脚本不是用Autoconf工具生成的，而是作者手工编写的。

到此，我们就完成了编译和安装Nginx服务器软件的环境准备工作。