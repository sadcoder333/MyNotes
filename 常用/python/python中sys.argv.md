### Python  sys.argv[\]用法

sys.argv[]是用来获取命令行参数的，sys.argv[0]表示代码本身文件路径，所以参数从**1**开始

#### 新建一个test.py文件，编辑代码如下：

```python
import sys

if __name__ == "__main__":
    for arg in sys.argv:
        print(arg)
```



#### 用命令行参数来执行这个python文件：

```python
python test.py arg1 arg2
```



#### 运行结果如下：

```
test.py
arg1
agr2
```



需要注意的是，在调用`python test.py arg1 arg2`命令行时，用`sys.argv`接收到的参数都是字符串，实际使用中可能需要手动转型，比如我们运行命令：

```
python test.py arg1 100
```

这里我们传递两个参数，第一个参数arg1为string类型，第二个参数为100，我们在使用的时候肯定需要转为数字类型

```python
import sys

if __name__ == "__main__":
    print(sys.argv[0]) # 输出test.py
    print(sys.argv[1]) # 输出arg1
    arg = sys.argv[2]  # arg为100的字符串
    num = int(arg)     # string转换为int
    print(num)
    
```

输出结果如下：

```
test.py
arg1
100
```

