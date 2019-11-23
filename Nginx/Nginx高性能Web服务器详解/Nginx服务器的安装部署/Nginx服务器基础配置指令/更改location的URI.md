# 更改location的URI

在location块中，除了使用root指令指明请求处理根目录，还可以使用alias指令改变location接收到的URI的请求路径，其语法结构为：
```
    alias path;
```
其中，path即为修改后的根路径。同样，此变量中也可以包含除了`$document_root`和`$realpath_root`之外的其他Nginx服务器预设变量。

这个指令的作用有点不好理解，我们来看一个示例：
```
    location ～ ^/data/(.+\.(htm|htm))$

    {
        alias /locationtest1/other/$1;
    }
```
当此location块接收到`/data/index.htm`的请求时，匹配成功，之后根据alias指令的配置，Nginx服务器将到`/locationtest1/other`目录下找到`index.htm`并响应请求。可以看到，通过alias指令的配置，根路径已经从/data更改为`/locationtest1/other`了。