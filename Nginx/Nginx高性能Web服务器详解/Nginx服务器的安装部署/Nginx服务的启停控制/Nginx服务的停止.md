# Nginx服务的停止

停止Nginx服务有两种方法：一种是快速停止；一种是平缓停止。快速停止是指立即停止当前Nginx服务正在处理的所有网络请求，马上丢弃连接，停止工作；平缓停止是指允许Nginx服务将当前正在处理的网络请求处理完成，但不再接收新的请求，之后关闭连接，停止工作。

停止Nginx服务的操作比较多。可以发送信号：
```
# ./sbin/Nginx -g TERM | INT | QUIT
```
其中，TERM和INT信号用于快速停止，QUIT用于平缓停止。
或者：
```
# kill TERM | INT | QUIT `/Nginx/logs/nginx.pid`
```
当然也可以使用kill命令向Nginx进程发送-9或者SIGKILL信号强制关闭Nginx服务：
```
# kill -9 | SIGKILL `/Nginx/logs/nginx.pid`
```
但不建议这样使用。