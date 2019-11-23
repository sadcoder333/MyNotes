# Nginx服务的重启

更改Nginx服务器的配置和加入新模块后，如果希望当前的Nginx服务应用新的配置或使新模块生效，就需要重启Nginx服务。当然我们可以先关闭Nginx服务，然后使用新的Nginx配置文件重启服务。这里主要介绍Nginx服务的平滑重启。

平滑重启是这样一个过程，Nginx服务进程接收到信号后，首先读取新的Nginx配置文件，如果配置语法正确，则启动新的Nginx服务，然后平缓关闭旧的服务进程；如果新的Nginx配置有问题，将显示错误，仍然使用旧的Nginx进程提供服务。
使用以下命令实现Nginx服务的平滑重启：
```
    # ./sbin/nginx -g HUP [-c newConfFile]
```

<b>HUP信号用于发送平滑重启信号。</b>

newConfFile，可选项，用于指定新配置文件的路径。
或者，使用新的配置文件代替了旧的配置文件后，使用：
```
    # kill HUP `/Nginx/logs/nginx.pid`
```
也可以实现平滑重启。