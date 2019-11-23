# Nginx服务器基础配置指令

从上面的内容我们知道，默认的Nginx服务器配置文件都存放在安装目录conf中，主配置文件名为nginx.conf。这一节，我们学习nginx.conf的内容和基本配置方法。

以下代码清单是默认的nginx.conf文件中的完整内容。

## 注意

在nginx.conf原始文件中，还包括注释内容，注释标志为“#”，由于篇幅所限，代码清单中将所有的注释去除。笔者添加的注释说明了各条语句的生效范围，让大家对指令的作用域有一个初步的了解，后面章节我们会进一步讲解。
```
    worker_processes   1;                         #全局生效
    events {
        worker_connections  1024;                 #在events部分中生效
    }
    http {
        include      mime.types;                  #以下指令在http部分中生效
        default_type  application/octet-stream;
        sendfile       on;
        keepalive_timeout  65;
        server {                                  #以下指令在http的server部分中生效
            listen      80;
            server_name  localhost;
            location / {                          #以下指令在http/server的location中生效
                root   html;
                index  index.html index.htm;
            }
            error_page   500 502 503 504  /50x.html;
            location = /50x.html {
                root   html;
            }
        }
    }
```
初始的Nginx服务器主配置文件比较长，不过结构和内容还是比较清晰的，以下我们分小节对上面的内容进行详细介绍。