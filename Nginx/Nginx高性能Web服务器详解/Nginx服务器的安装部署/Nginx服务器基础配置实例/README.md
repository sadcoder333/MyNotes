# Nginx服务器基础配置实例

上一节我们对Nginx服务器默认配置文件的结构和涉及的基本指令做了详尽的阐述。通过对这些指令的合理配置，我们就可以让一台Nginx服务器正常工作，并提供基本的Web服务器功能了。

在本节中，笔者为大家准备了一个比较完整和最简单的基础配置实例，并进行了必要的注释说明，帮助大家在整体上对nginx.conf文件的结构加深理解，同时巩固上一节学习的指令及其配置。

以下是笔者准备的nginx.conf文件的完整内容：
```
#### 全局块 开始 #####
                                # 配置允许运行Nginx服务器的用户和用户组
user nobody nobody;
                                # 配置允许Nginx进程生成的worker process数
worker_processes  3;
                                # 配置Nginx服务器运行对错误日志存放路径
error_log  logs/error.log;
                                # 配置Nginx服务器运行时的pid文件存放路径和名称
pid    nginx.pid;
##### 全局块 结束 #####

#### events块 开始 ####
events
{
                                # 配置事件驱动模型
    use epoll;
                                # 配置最大连接数
    worker_connections  1024;
}
#### events块 结束 ####

#### http块 开始 ####
http {
                                # 定义MIME-Type
    include      mime.types;
    default_type  application/octet-stream;
                                # 配置允许使用sendfile方式传输
    sendfile  on;
                                # 配置连接超时时间
    keepalive_timeout  65;
                                # 配置请求处理日志的格式
    log_format  access.log
'$remote_addr-[$time_local]-"$request"-"$http_user_agent"';
    
    #### server块 开始 ####

    ## 配置虚拟主机 myServer1
    server {
                                    # 配置监听端口和主机名称（基于名称）
        listen      8081;
        server_name   myServer1;
                                    # 配置请求处理日志存放路径
        access_log  /myweb/server1/log/access.log;
                                    # 配置错误页面
        error_page  404   /404.html;
                                    # 配置处理/server1/location1请求的location

        location /server1/location1 {
            root  /myweb;
            index  index.svr1-loc1.htm;
        }
                                    # 配置处理/server1/location2请求的location
        location /server1/location2 {
            root  /myweb;
            index  index.svr1-loc2.htm;
        }
    }

    ## 配置虚拟主机 myServer2
    server {
        listen      8082;
        server_name  192.168.1.3;
        access_log  /myweb/server2/log/access.log;
        error_page  404  /404.html;      #对错误页面404.html做了定向配置
        
        location /server2/location1 {
            root  /myweb;
            index  index.svr2-loc1.htm;
        }
        
        location /svr2/loc2 {
            alias  /myweb/server2/location2/;         #对location的URI进行更改
            index  index.svr2-loc2.htm;
        }
                                    # 配置错误页面转向
        location = /404.html {
            root  /myweb/;
            index 404.html;
        }
    }
    #### server块 结束 ####

}

#### http块 结束 ####
```
在该实例中，我们配置了两个虚拟主机myServer1和myServer2，前者是基于名称的，后者是基于IP的。在每个虚拟主机里，笔者又分别使用了location块对不同的请求进行处理。主机myServer2除了对一般的请求进行处理外，还对错误页面404.html做了定向配置，指向笔者自定义的404处理页面。

笔者为了测试此Nginx配置，构建了一个十分简单的静态网站站点。我们没有必要关心站点的具体内容，主要看一下它的目录组织结构：
```
myweb
    404.html
    server1
        location1
            index.svr1-loc1.htm
        location2
            index.svr1-loc2.htm

        log
            access.log
    server2
        location1
            index.svr2-loc1.htm
        location2
            index.svr2-loc2.htm
        log
            access.log
```
上面的目录结构是比较清晰的，建议读者结合网站结构阅读上面的配置文件实例，加深理解。在结构中需要注意的是404.html这个文件。如果不使用myServer2中对错误页面定向的方法，而只是像myServer1那样简单设置错误页面的路径，那么Nginx服务器会在安装路径的html目录下的相关路径中寻找错误页面。在介绍error_page指令时我们已经提到过这一点，在这里再次强调一下。在该实例中出现的其他指令和配置细节都在前面详细讲解过，就不在此赘述了。

以下是笔者测试通过Nginx服务器访问myweb站点的一些结果。