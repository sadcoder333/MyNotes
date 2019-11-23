# Linux版本的编译和安装-Nginx源代码的编译和安装

得到了Nginx软件的Makefile文件后，我们就可以编译源代码了。保持当前工作路径仍为/Nginx_123/Nginx_123_ Compile/nginx-1.2.3/目录，使用make命令进行编译：
```
make                                                            //编译
```

同样，我们可以在屏幕上看到Nginx源代码的编译全过程。

编译顺利完成以后，使用make的install命令安装Nginx软件：
```
make install                                                        //安装
```

命令运行完成后，将当前工作目录定位到/nginx下，可以对Nginx服务器安装后的全部资源进行查看：
```
cd /Nginx;
ls -l
总用量 36
drwx------.  2 nobody root 4096 1月  7 14:52 client_body_temp
drwxr-xr-x.  2 root  root 4096 1月  9 17:11 conf
drwx------.  2 nobody root 4096 1月  7 14:52 fastcgi_temp
drwxr-xr-x.  2 root  root 4096 1月  7 14:48 html
drwxr-xr-x.  2 root  root 4096 1月  18 11:46 logs
drwx------. 12 nobody root 4096 1月  7 16:06 proxy_temp
drwxr-xr-x.  2 root  root 4096 1月  7 14:48 sbin
drwx------.  2 nobody root 4096 1月  7 14:52 scgi_temp
drwx------.  2 nobody root 4096 1月  7 14:52 uwsgi_temp
```

注意
>如果在编译过程中出现了源代码的编译错误，屏幕上会出现错误信息，你可以对这些信息认真查阅，并结合表2.1的相关内容解决编译错误。根据笔者的经验，编译错误多是因缺少一些模块的支持库引起的，比如笔者曾经遇到过缺少pcre库等问题引起的编译错误。如果遇到此错误，则可以下载pcre的源代码包，并复制到某目录下，然后为configure指定--with-pcre=＜dir＞后生成Makefile文件。

另外，在没有改动源代码的情况下如果需要重新编译和安装Nginx软件，就不必再使用configure脚本自动生成Makefile了。可以先使用以下命令删除上次安装的Nginx软件：
```
rm -rf /Nginx/*
```
然后定位到nginx-1.2.3.tar.gz解压目录，清除上次编译的遗留文件：
```
cd /Nginx_123/Nginx_123_ Compile/nginx-1.2.3/; make clean
```
之后再使用以下命令进行编译和安装：
```
make; make install
```
到此为止，我们就安装好了一个最基本的Nginx服务器，其安装路径为/Nginx目录。我们来看一下Nginx服务器的安装目录中包含了哪些内容：

```
#ls *

conf:
fastcgi.conf    fastcgi_params    koi-utf  mime.types     nginx.conf
scgi_params   uwsgi_params    win-utf    fastcgi.conf.default
fastcgi_params.default
koi-win   mime.types.default   nginx.conf.default   scgi_params.default
uwsgi_params.default
html:
50x.html  index.html
logs:
access.log  error.log
sbin:
nginx
```

Nginx服务器的安装目录中主要包括了conf、html、logs和sbin等4个目录。

## conf目录

conf目录中存放了Nginx的所有配置文件。其中，nginx.conf文件是Nginx服务器的主配置文件，其他配置文件是用来配置Nginx的相关功能的，比如，配置fastcgi使用的fastcgi.conf和fastcgi_params两个文件，这些将在专门的章节中详细讲解。在此目录下，所有的配置文件都提供了以.default结尾的默认配置文件，方便我们将配置过的.conf文件恢复到初始状态。

## html目录

html目录中存放了Nginx服务器在运行过程中调用的一些html网页文件。我们来简单看一下其中的内容。

首先是index.html文件。
```
#cat /Nginx/html/index.html                                      //打印文件内容
＜html＞
    ＜head＞
        ＜title＞Welcome to nginx!＜/title＞
    ＜/head＞
    ＜body bgcolor="white" text="black"＞
        ＜center＞＜h1＞Welcome to nginx!＜/h1＞＜/center＞
    ＜/body＞
＜/html＞
```
从内容来看，index.html是在浏览器页面上打印出“Welcome to nginx!”这样一句话。可以推测一下，这个文件应该是Nginx服务器运行成功后，默认调用的网页，提示用户Nginx服务器运行成功了吧？我们到学习Nginx服务器启动的相关内容时再来验证推测是否正确。
接下来再看50x.html文件的内容：
```
#cat /Nginx/html/50x.html

＜html＞
    ＜head＞
        ＜title＞The page is temporarily unavailable＜/title＞
            ＜style＞
        body { font-family: Tahoma, Verdana, Arial, sans-serif; }
            ＜/style＞
    ＜/head＞
    ＜body bgcolor="white" text="black"＞
        ＜table width="100%" height="100%"＞
            ＜tr＞
                ＜td align="center" valign="middle"＞
            The page you are looking for is temporarily unavailable.＜br/＞
            Please try again later.
                ＜/td＞
            ＜/tr＞
        ＜/table＞
    ＜/body＞
＜/html＞
```
50x.html是在浏览器页面上打印出“The page you are looking for is temporarily unavailable. Please try again later.”这样一句话。很显然，Nginx在出现某些问题时将会调用这个页面。

事实上，我们还可以在html目录下自定义一些网页文件，并在配置文件中配置发生什么情况时转到相应的文件。这些技巧我们在以后的章节中会逐步涉及。

## logs目录

logs目录，顾名思义，是用来存放Nginx服务器的日志的。目前Nginx服务器没有启用，因此目录是空的。Nginx的日志功能比较强大，有不同的种类，并且可以自定义输出格式内容等，我们在相关的章节详细阐述。

## sbin目录

最后是sbin目录，目前其中只有nginx一个文件，这就是Nginx服务器的主程序了。