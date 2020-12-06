os.system用于执行cmd命令，常见的比如调用FFmpeg命令行，这时候可能需要各种参数来拼接命令。

这里简单起见，调用一个java查看版本的命令，代码如下：

```
import os

def run_cmd():
    os.system('java -version')

if __name__ == "__main__":
    run_cmd()
```



输出结果如下：

```
java version "1.8.0_181"
Java(TM) SE Runtime Environment (build 1.8.0_181-b13)
Java HotSpot(TM) 64-Bit Server VM (build 25.181-b13, mixed mode)
```

