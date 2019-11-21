# Lighttpd

Lighttpd服务器来自德国的一个开源轻量级Web服务器软件，它在2004年左右开始取得了高速发展。Lighttpd，是Light footprint和httpd的结合，读音同Lighty。在Lighttpd的官方网站[http://www.lighttpd.net](http://www.lighttpd.net)中有这样一段介绍：

>With a small memory footprint compared to other web-servers, effective management of the cpu-load, and advanced feature set lighttpd is the perfect solution for every server that is suffering load problems.

由此可见Lighttpd的名字就是此服务器设计理念的完美体现。

根据Netcraft曾经发布的数据调查显示，2007年1月，全球使用Lighttpd的网站为170000家，2月这个数字就达到了7000000，在短短的一个月内惊人地增长了400%！当时，包括一些著名的网站，如YouTube、Wikipedia、Meebo、Yahoo! Messenger、Windows Live Messenger、ICQ、AIM等，以及国内的网易新闻、六间房、56.COM、豆瓣、新浪博客、迅雷在线、花瓣网等都使用它作为服务器软件。

Lighttpd的急速发展得益于它专门针对高性能网站，提供了一套安全、快速、兼容性良好并且灵活的Web Server环境。同时，它具有非常低的内存开销、CPU占用率低以及模块丰富等特点，支持FastCGI、Output Compress（输出压缩）、URL重写等绝大多数Apache具有的重要功能，是Apache的绝好替代者。

作为轻量级服务器，Lighttpd与Apache等大型Web服务器软件相比，其在功能上存在不足和部分缺陷，比如Proxy功能不完善、对编码支持不完善等缺点。