# 标准C时间与日期函数

 

## asctime 

语法: 

``` 
  #include <time.h>
  char *asctime( const struct tm *ptr );
```

功能： 函数将ptr所指向的时间结构转换成下列字符串： 
```
    day month date hours:minutes:seconds year\n\0
```
例如: 
```
    Mon Jun 26 12:03:53 2000
```
>相关主题:
localtime(), gmtime(), time(), and ctime(). 




## clock 

语法: 

``` 
  #include <time.h>
  clock_t clock( void );
``` 

功能：函数返回自程序开始运行的处理器时间，如果无可用信息，返回-1。 转换返回值以秒记, 返回值除以CLOCKS_PER_SECOND. (注: 如果编译器是POSIX兼容的, CLOCKS_PER_SECOND定义为1000000.) 

>相关主题:
time(), asctime(), and ctime(). 




## ctime 

语法: 

``` 
  #include <time.h>
  char *ctime( const time_t *time );
``` 

功能：函数转换参数time为本地时间格式：
```
    day month date hours:minutes:seconds year\n\0
ctime() 等同 

    asctime( localtime( tp ) );
```
>相关主题:
localtime(), gmtime(), time(), and asctime(). 




## difftime 

语法: 
```
  #include <time.h>
  double difftime( time_t time2, time_t time1 );
``` 

功能：函数返回时间参数time2和time1之差的秒数表示。

>相关主题:
localtime(), gmtime(), time(), and asctime(). 




## gmtime 

语法: 

``` 
  #include <time.h>
  struct tm *gmtime( const time_t *time );
``` 

功能：函数返回给定的统一世界时间（通常是格林威治时间），如果系统不支持统一世界时间系统返回NULL。 警告! 

>相关主题:
localtime(), time(), and asctime(). 




## localtime 

语法: 

``` 
  #include <time.h>
  struct tm *localtime( const time_t *time );
``` 

功能：函数返回本地日历时间。警告！ 

>相关主题:
gmtime(), time(), and asctime(). 




## mktime 

语法: 

``` 
  #include <time.h>
  time_t mktime( struct tm *time );
``` 

功能：函数转换参数time 类型的本地时间至日历时间，并返回结果。如果发生错误，返回－1。 

>相关主题:
time(), gmtime(), asctime(), and ctime(). 




## strftime 

语法: 

``` 
  #include <time.h>
  size_t strftime( char *str, size_t maxsize, const char *fmt, struct tm *time );
``` 

功能：函数按照参数fmt所设定格式将time类型的参数格式化为日期时间信息，然后存储在字符串str中（至多maxsize 个字符）。用于设定时间不同类型的代码为： 

|代码|含义|
|---|---| 
|%a|星期的缩略形式|
|%A|星期的完整形式|
 |%b|月份的缩略形式|
|%B|月份的完整形式|
 |%c|月份的缩略形式|
 |%d|月中的第几天(1-31)|
|%H|小时, 24小时格式 (0-23)|
 |%I|小时, 12小时格式  (1-12)|
|%j|年中的第几天(1-366)|
 |%m|月份 (1-12). Note: 某些版本的Microsoft Visual C++ 可能使用取值范围0-11.|
|%M|分钟(0-59)|
|%p|本地时间的上午或下午（AM or PM）
|%S|秒钟(0-59)
|%U|年中的第几周，星期天是一周的第一天
|%w|星期几的数字表示(0-6, 星期天=0)
|%W|一年中的第几周，星期天是一周的第一天
|%x|标准日期字符串
|%X|标准时间字符串
|%y|年(0-99)
|%Y|用CCYY表示的年（如：2004）
 |%Z|时区名
|%%|百分号
 

函数strftime()返回值为处理结果字符串str中字符的个数，如果发生错误返回零。

>相关主题:
time(), localtime(), and gmtime(). 




## time 

语法: 

``` 
  #include <time.h>
  time_t time( time_t *time );
``` 

功能： 函数返回当前时间，如果发生错误返回零。如果给定参数time ，那么当前时间存储到参数time中。 

>相关主题:
localtime(), gmtime(), strftime(), ctime(),
