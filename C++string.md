## 引入头文件和命名空间

```
#include <string>

using namespace std;
```

## string构造
```
string s1; //声明一个空字符串
string s2(s1); 


const char *str = "test string";
string s3(str);   //通过char *构造string



```

## string 和char* 转换
```
char *str = "hello";
string s1(str);   //char *转化为string

string s2 = "world"; 
const char *s3 = s2.c_str();    //string转const char*

char *s4 = (const_cast)s2.c_str(); //string转char*
```


## string的拼接
```
```