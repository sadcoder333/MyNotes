# 配置允许sendfile方式传输文件

在Apache、lighttd等Web服务器配置中，都有和sendfile相关的配置，这里主要学习一下配置sendfile传输方式的相关指令sendfile和sendfile_max_chunk以及它们的语法结构：
```
    sendfile on | off;
```

用于开启或者关闭使用sendfile()传输文件，默认值为off，可以在http块、server块或者location块中进行配置。
```
    sendfile_max_chunk size;
```
其中，size值如果大于0，Nginx进程的每个worker process每次调用sendfile()传输的数据量最大不能超过这个值；如果设置为0，则无限制。默认值为0。此指令可以在http块、server块或location块中配置。

下面是第二个指令的配置示例：
```
    sendfile_max_chunk 128k;
```