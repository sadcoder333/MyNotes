# 基于密码配置Nginx的访问权限

Nginx还支持基于HTTP Basic Authentication协议的认证。该协议是一种HTTP性质的认证办法，需要识别用户名和密码，认证失败的客户端不拥有访问Nginx服务器的权限。该功能由HTTP标准模块ngx_http_auth_basic_module支持，这里有两个指令需要学习。

## auth_basic指令

用于开启或者关闭该认证功能，语法结构为：
```
    auth_basic string | off;
```
- string，开启该认证功能，并配置验证时的指示信息。
- off，关闭该认证功能。

## auth_basic_user_file指令

用于设置包含用户名和密码信息的文件路径，语法结构为：
```
    auth_basic_user_file file;
```

其中，file为密码文件的绝对路径。

这里的密码文件支持明文或者密码加密后的文件。明文的格式如下所示：
```
    name1:password1
    name2:password2:comment
    name3:password3
```
加密密码可以使用crypt()函数进行密码加密的格式，在Linux平台上可以使用htpasswd命令生成。在PHP和Perl等语言中，也提供crypt()函数。使用htpasswd命令的一个示例为：
```
    # htpasswd  -c  -d  /nginx/conf/pass_file  username
```
运行后输入密码即可。