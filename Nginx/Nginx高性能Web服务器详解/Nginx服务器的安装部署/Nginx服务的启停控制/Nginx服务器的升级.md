# Nginx服务器的升级

如果要对当前的Nginx服务器进行版本升级，应用新模块，最简单的办法是停止当前Nginx服务，然后开启新的Nginx服务，但这样就会导致在一段时间内，用户无法访问服务器。为了解决这个问题， Nginx服务器提供平滑升级的功能。

平滑升级的过程是这样的，Nginx服务接收到USR2信号后，首先将旧的nginx.pid文件（如果在配置文件中更改过这个文件的名字，也是相同的过程）添加后缀.oldbin，变为nginx.pid.oldbin文件；然后执行新版本Nginx服务器的二进制文件启动服务。如果新的服务启动成功，系统中将有新旧两个Nginx服务共同提供Web服务。之后，需要向旧的Nginx服务进程发送WINCH信号，使旧的Nginx服务平滑停止，并删除nginx.pid.oldbin文件。在发送WINCH信号之前，可以随时停止新的Nginx服务。

## 注意

为了实现Nginx服务器的平滑升级，新的服务器安装路径应该和旧的保持一致。因此建议用户在安装新服务器之前先备份旧服务器。如果由于某种原因无法保持新旧服务器安装路径一致，则可以先使用以下命令将旧服务器的安装路径更改为新服务器的安装路径：
```
# ./Nginx/nginx -p newInstallPath
```
其中，newInstallPath为新服务器的安装路径。之后，备份旧服务器，安装新服务器即可。

做好准备工作以后，使用以下命令实现Nginx服务的平滑升级：
```
# ./sbin/Nginx -g USR2
```
其中，USR2信号用于发送平滑升级信号。或者，使用：
```
# kill USR2 `/Nginx/logs/nginx.pid`
```
通过ps -ef | grep nginx查看新的Nginx服务启动正常，再使用：
```
# ./sbin/Nginx -g WINCH
```
其中，WINCH信号用于发送平滑停止旧服务信号。或者，使用：
```
# kill WINCH `/Nginx/logs/nginx.pid`
```
这样就在不停止提供Web服务的前提下完成了Nginx服务器的平滑升级。