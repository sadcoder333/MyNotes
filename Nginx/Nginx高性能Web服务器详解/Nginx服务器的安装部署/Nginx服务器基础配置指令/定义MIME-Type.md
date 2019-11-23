# 定义MIME-Type

我们知道，在常用的浏览器中，可以显示的内容有HTML、XML、GIF及Flash等种类繁多的文本、媒体等资源，浏览器为区分这些资源，需要使用MIME Type。换言之，MIME Type是网络资源的媒体类型。Nginx服务器作为Web服务器，必须能够识别前端请求的资源类型。

在默认的Nginx配置文件中，我们看到在http全局块中有以下两行配置：
```
    include mime.types;
    default_type application/octet-stream;
```
第一行从外部引用了mime_types文件，我们来看一下它的内容片段：
```
    # cat mime.types
    types {
        text/html                        html htm shtml;
        …
        image/gif                        gif;
        …
        application/x-javascript         js;
        …
        audio/midi                       mid midi kar;
        …
        video/3gpp                       3gpp 3gp;
        …
    }
```
从mime_types文件的内容片段可以看到，其中定义了一个types结构，结构中包含了浏览器能够识别的MIME类型以及对应于相关类型的文件后缀名。由于mime_types文件是主配置文件应用的第三方文件，因此，types也是Nginx配置文件中的一个配置块，我们可以称之为types块，其用于定义MIME类型。MIME的知识不是本文的重点，不在这里详述，感兴趣的读者可以自行阅读相关书籍。

第二行中使用指令default_type配置了用于处理前端请求的MIME类型，其语法结构为：
```
    default_type mime-type;
```
其中，mime-type为types块中定义的MIME-type，如果不加此指令，默认值为text/plain。此指令还可以在http块、server块或者location块中进行配置。