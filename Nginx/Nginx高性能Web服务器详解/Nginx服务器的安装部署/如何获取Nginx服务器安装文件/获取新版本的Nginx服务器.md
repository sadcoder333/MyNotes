# 获取新版本的Nginx服务器

Nginx的官方下载网站为[http://nginx.org/en/download.html](http://nginx.org/en/download.html)。打开网站，下载部分的内容如图2.1所示。可以看到，网页上提供了Nginx服务器三种版本的下载，分别是开发版本（Development version）、稳定版本（Stable version）和过期版本（Legacy versions）。三种版本的差异和选择在第1章中已经介绍过，这里不再赘述。本页提供下载的各类版本均为Nginx的较新版本。其中，开发版本同时也是Nginx全部版本中最新的版本。

下面分别介绍页面上下载部分各链接的具体含义：

- “CHANGES-x.x”链接，记录的是对应版本的功能变更日志。包括新增功能、功能的优化和功能缺陷的修复等。

- 紧接着“CHANGES-x.x”链接后面的“nginx-x.x.x”链接，是Nginx服务器的Linux版本下载链接。右击链接，选择“另存为”命令或者选择下载专用工具就可以获取到Nginx服务器的Linux版本。得到的文件的后缀名为.tar.gz。

- “pgp”链接，记录的是提供下载的版本使用PGP加密自由软件GnuPG计算后的签名。PGP可以解释为Pretty Good Privacy，是PGP公司的加密或签名工具套件。点击链接进入相关页面，可以查看GnuPG针对本下载版本的签名，以及执行本次计算的GnuPG软件版本号。这些数据可以用于下载文件的验证。

- “nginx/Windows-x.x.x”链接，是Nginx服务器的Windows版本下载链接，下载方法和Linux版本相同。得到的文件的后缀名为.zip。