# 配置Nginx进程PID存放路径

Nginx进程作为系统的守护进程运行，我们需要在某文件中保存当前运行程序的主进程号。Nginx支持对它的存放路径进行自定义配置，指令是pid，其语法格式为：
```
pid file ;
```

其中，file指定存放路径和文件名称。

>配置文件默认将此文件存放在Nginx安装目录logs下，名字为nginx.pid。path可以是绝对路径，也可以是以Nginx安装目录为根目录的相对路径。比如要把nginx.pid放置到Nginx安装目录sbin下，文件名为web_nginx，则可以使用以下配置：
```
pid sbin/web_nginx
```

## 注意

在指定[path]的时候，一定要包括文件名，如果只设置了路径，没有设置文件名，则会报以下错误：
```
nginx: [emerg] open() "/Nginx/logs/" failed (21: Is a directory)
```

此指令只能在全局块中进行配置。