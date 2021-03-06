# 获取Nginx服务器的历史版本

在第1章中，我们了解到Nginx服务器包含众多的历史版本。Nginx官方网站没有显式提供下载历史版本的链接，但是如果由于特殊的需求需要获取Nginx服务器的历史版本，该怎么做呢？

笔者为大家介绍一个可以下载Nginx服务器全部历史版本的链接，即[http://nginx.org/download](http://nginx.org/download)。打开此网页，可以看到Nginx全部历史版本的列表，从nginx-0.1.0到nginxnginx-1.3.5一应俱全，下载方式和上面介绍的新版本Nginx服务器软件下载方式相同。

仔细查看版本列表，可以发现以nginx-0.7.52为分界线，之前的低版本只提供后缀名为.tar.gz的Linux版本，从nginx-0.7.52开始同时提供后缀名为.zip的Windows版本，出现这种现象的原因我们在第1章回顾Nginx服务器发展历史时已经说明。从nginx-0.7.64开始，还提供了后缀名为.asc的文件，该文件记录了Linux版本PGP加密自由软件签名数据。