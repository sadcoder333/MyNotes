# Nignx诞生记

Nginx（engine-x）是由1994年毕业于俄罗斯国立莫斯科鲍曼技术大学的Igor Sysoev为俄罗斯访问量居首的Rambler.ru站点[www.rambler.ru](www.rambler.ru)设计开发的。开发工作从2002年开始，第一次正式公开发布是在2004年10月4日，版本号为0.1.0。

Nginx是一款免费开源的高性能HTTP服务器及反向代理服务器（Reverse Proxy）产品，同时，它还可以提供IMAP/POP3代理服务等功能。在实际的使用中，Nginx还可以提供更多更丰富的功能，我们将在下一节介绍它的功能。

Nginx的官方网站为[http://www.nginx.org](http://www.nginx.org)，同时Wiki为Nginx开设了专门的介绍页面，链接为[http://wiki.nginx.org/Main](http://wiki.nginx.org/Main)。本文引述的部分背景信息来源于这两个网站。大家可以由此获取更多相关背景知识。

到目前为止，Nginx已经在俄罗斯第一大网站Rambler.ru上运行了近9个年头。在这段时间中， Nginx不断成长和发展，以其稳定的性能、丰富的功能集、低系统资源的消耗而逐渐被全球Web服务器使用者认可，在全球的市场份额节节攀升。根据Wiki的资料显示，目前全球活跃的网站中，有12.18% （大约为22200000个）的网站是由Nginx提供服务。而根据上一节中Netcraft公布的全球主流Web服务器最新数据显示，Nginx的发展势头仍然良好。

为什么Nginx会成为众多Web服务器产品中的后起之秀呢？Nginx到底能给我们带来怎样不同寻常的服务呢？在回答这些问题之前，我们先来简单梳理一下Nginx的历史版本和更新，从中感受Nginx快速成长的历程