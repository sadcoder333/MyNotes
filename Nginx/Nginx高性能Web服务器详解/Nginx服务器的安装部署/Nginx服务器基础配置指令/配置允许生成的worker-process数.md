# 配置允许生成的worker-process数

>worker process是Nginx服务器实现并发处理服务的关键所在。从理论上来说，worker process的值越大，可以支持的并发处理量也越多，但实际上它还要受到来自软件本身、操作系统本身资源和能力、硬件设备（如CPU和磁盘驱动器）等的制约。后面会用专门的章节来讨论Nginx服务器的高级配置。

配置允许生成的worker process数的指令是worker_processes，其语法格式为：
```
    worker_processes number | auto;
```

- number，指定Nginx进程最多可以产生的worker process数。
- auto，设置此值，Nginx进程将自动检测。

在默认的配置文件中，number=1。启动Nginx服务器以后，使用以下命令可以看到Nginx服务器除了主进程master process ../sbin/nginx之外，还生成了一个worker process：
```
#ps ax | grep nginx
8579 ?       Ss    0:00 nginx: master process ../sbin/nginx
8580 ?       S     0:00 nginx: worker process
```

如果将number改为3，重新运行Nginx进程，再次使用以上命令，则可以看到此时的Nginx服务器除了主进程master process ../sbin/nginx之外，已经生成了三个worker process：
```
#ps ax | grep nginx
8626 ?       Ss    0:00 nginx: master process ../sbin/nginx
8627 ?       S     0:00 nginx: worker process
8628 ?       S     0:00 nginx: worker process
8629 ?       S     0:00 nginx: worker process
```
此指令只能在全局块中设置。