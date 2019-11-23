# Nginx服务的启动

在Linux平台下，启动Nginx服务器直接运行安装目录下sbin目录中的二进制文件即可。这里简要介绍一下二进制文件nginx的相关用法。将当前工作目录定位到Nginx安装目录下，运行以下命令：
```
    # ./sbin/nginx -h
    nginx version: nginx/1.2.4
    Usage: nginx [-?hvVtq] [-s signal] [-c filename] [-p prefix] [-g directives]
    Options:
      -?,-h          : this help     显示该帮助信息
      -v             : show version and exit 打印版本号并退出
      -V             : show version and configure options then exit打印版本号和配置并退出
      -t             : test configuration and exit    测试配置正确性并退出
      -q             : suppress non-error messages during configuration testing   测试
    配置时只显示错误
      -s signal      : send signal to a master process: stop, quit, reopen, reload向主
    进程发送信号
      -p prefix      : set prefix path (default: /Nginx/bin/)    指定Nginx服务器路径前缀
      -c filename    : set configuration file (default: conf/nginx.conf)  指定Nginx配
    置文件路径
      -g directives  : set global directives out of configuration file    指定Nginx附
    加配置文件路径
```

接下来对帮助信息中允许使用的参数逐条进行分析。

在nginx的帮助信息中可以看到，nginx可以使用一些参数。“-h”或者“-？”用来打印二进制文件nginx的用法，也就是当前显示的内容；“-v”用来显示Nginx服务器的版本号；“-V”除了显示版本号，还显示Nginx服务器编译情况，笔者测试输出为：
```
# ./nginx -V
nginx version: nginx/1.2.3

built by gcc 4.1.2 20070115 (prerelease) (Fedora Linux)
configure arguments: --prefix=/Nginx
“-t”检查Nginx服务器配置文件是否有语法错误，可以与“-c”联用，使输出内容更详细，这对查找配置文件中的语法错误很有帮助，如果检查通过，将显示类似下面的信息：

# ./nginx -t
nginx: the configuration file /Nginx/conf/nginx.conf syntax is ok
nginx: configuration file /Nginx/conf/nginx.conf test is successful
```
“-q”与“-t”联用，如果配置文件无错误，将不输出上面的内容；“-s signal”用来向Nginx服务的主进程发送信号，关于信号控制，查看上一小节的内容；“-p prefix”用来改变Nginx的安装路径，常用在平滑升级Nginx服务器的场合；“-c filename”用来指定启动Nginx服务使用的配置文件；“-g directives”用来补充Nginx配置文件，向Nginx服务指定启动时应用于全局的配置。
介绍了以上二进制文件nginx的用法后，相信读者已经知道如何启动Nginx服务了。我们使用默认的配置文件，因此直接运行：
```
# ./sbin/Nginx
```
如果没有任何错误信息输出，Nginx服务就启动了。可以使用ps -ef | grep nginx命令查看Nginx服务的进程状态。