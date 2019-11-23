# 基于IP的虚拟主机配置

Linux操作系统支持IP别名的添加。配置基于IP的虚拟主机，即为Nginx服务器提供的每台虚拟主机配置一个不同的IP，因此需要将网卡设置为同时能够监听多个IP地址。在Linux平台中可以使用ifconfig工具为同一块网卡添加多个IP别名。

笔者的Linux平台上当前的网络配置为：
```
#ifconfig                                                    #打印网络配置信息
eth1     Link encap:Ethernet  HWaddr 00:0C:29:AA:6A:19
        inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
        inet6 addr: fe80::20c:29ff:feaa:6a19/64 Scope:Link
        UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
        RX packets:30367 errors:0 dropped:0 overruns:0 frame:0
        TX packets:15372 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:1000
        RX bytes:3665744 (3.4 Mb)  TX bytes:2439099 (2.3 Mb)
lo       Link encap:Local Loopback
        inet addr:127.0.0.1  Mask:255.0.0.0

        inet6 addr: ::1/128 Scope:Host
        UP LOOPBACK RUNNING  MTU:16436  Metric:1
        RX packets:133 errors:0 dropped:0 overruns:0 frame:0
        TX packets:133 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:0
        RX bytes:9512 (9.2 Kb)  TX bytes:9512 (9.2 Kb)
```
eth1为使用中的网卡，其IP值为`192.168.1.3`。现在笔者需要为eth1添加两个IP别名`192.168.1.31`和`192.168.1.32`，分别用于Nginx服务器提供的两个虚拟主机，需要执行以下操作：
```
#ifconfig eth1:0 192.168.1.31 netmask 255.255.255.0 up
#ifconfig eth1:1 192.168.1.32 netmask 255.255.255.0 up
```
命令中的up表示立即启用此别名。

此时笔者的Linux平台的网络配置为：
```
#ifconfig
eth1     Link encap:Ethernet  HWaddr 00:0C:29:AA:6A:19
        inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
        inet6 addr: fe80::20c:29ff:feaa:6a19/64 Scope:Link
        UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
        RX packets:31581 errors:0 dropped:0 overruns:0 frame:0
        TX packets:15558 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:1000
        RX bytes:3749064 (3.5 Mb)  TX bytes:2461311 (2.3 Mb)
eth1:0   Link encap:Ethernet  HWaddr 00:0C:29:AA:6A:19
        inet addr:192.168.1.31  Bcast:192.168.1.255  Mask:255.255.255.0
        UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
eth1:1   Link encap:Ethernet  HWaddr 00:0C:29:AA:6A:19
        inet addr:192.168.1.32  Bcast:192.168.1.255  Mask:255.255.255.0
        UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
lo       Link encap:Local Loopback
        inet addr:127.0.0.1  Mask:255.0.0.0
        inet6 addr: ::1/128 Scope:Host
        UP LOOPBACK RUNNING  MTU:16436  Metric:1
        RX packets:133 errors:0 dropped:0 overruns:0 frame:0
        TX packets:133 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:0
        RX bytes:9512 (9.2 Kb)  TX bytes:9512 (9.2 Kb)
```
可以看到，eth1增加了两个别名，分别为eth1:0和eth1:1，IP也分别是我们希望得到的结果。

## 注意

按照如上方法为eth1设置的别名在系统重启后将不予保存，需要重新设置。为了做到一劳永逸，我们可以将以上两条命令添加到Linux系统的启动脚本rc.local中。在笔者的系统中运行：
```
# echo "ifconfig eth1:0 192.168.1.31 netmask 255.255.255.0 up" ＞＞ /etc/rc.local
# echo "ifconfig eth1:1 192.168.1.32 netmask 255.255.255.0 up" ＞＞ /etc/rc.local
```

这样，在系统重启后，eth1的别名就自动设置好了。

为网卡设置好别名以后，就可以为Nginx服务器配置基于IP的虚拟主机了。使用的指令和配置基于名称的虚拟主机的指令是相同的，即server_name，语法结构也相同。而且不需要考虑通配符或者正则表达式的问题。

笔者的Nginx配置文件中配置了两台基于IP的虚拟主机，相关的配置片段为：
```
    …
    http
    {
        …
        server                                                       #第一台虚拟主机
        {
            listen: 80;
            server_name: 192.168.1.31;
            …
        }
        server                                                       #第二台虚拟主机
        {
            listen: 80;
            server_name: 192.168.1.32;
            …
        }
        …
    }
```

经过以上的配置，来自`192.168.1.31`的前端请求将由第一台虚拟主机接收和处理，来自`192.168.1.32`的前端请求将由第二台虚拟主机接收和处理。