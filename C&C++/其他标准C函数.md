# 其他标准C函数

## abort 
语法: 
```
   #include <stdlib.h>  
   void abort( void ); 
```
功能： 终止程序的执行。返回值依赖于执行，可以通过返回值显示错误。 

>相关主题:
exit() and atexit(). 


## assert 

语法: 
```
   #include <assert.h>  
   void assert( int exp ); 
```
功能： 宏assert()用于错误检测。如果表达式的结果为零，宏写错误信息到STDERR并退出程序执行。如果宏NDEBUG已经定义，宏assert()将被忽略。 

>相关主题:
abort() 


## atexit 

语法: 
```
   #include <stdlib.h>  
   int atexit( void (*func)(void) );
```  
功能： 当程序终止执行时，函数调用函数指针func所指向的函数。可以执行多重调用(至少32个)，这些函数以其注册的倒序执行。执行成功返回零值，失败则返回非零值。 

>相关主题:
exit() and abort(). 


## bsearch 

语法: 
```
   #include <stdlib.h>  
   void *bsearch( const void *key, const void *buf, size_t num, size_t size, int (*compare)(const void *, const void *) ); 
```
功能： 函数用折半查找法在从数组元素buf[0]到buf[num-1] 匹配参数key。如果函数compare 的第一个参数小于第二个参数，返回负值；如果等于返回零值；如果大于返回正值。数组buf 中的元素应以升序排列。函数bsearch()的返回值是指向匹配项，如果没有发现匹配项，返回NULL。 

>相关主题:
qsort(). 

## exit 

语法: 
```
   #include <stdlib.h>  
   void exit( int exit_code ); 
```  
功能：终止程序的执行。参数exit_code 传递给返回值，通常零值表示正常结束，非零值表示应错误返回。 

>相关主题:
atexit() and abort(). 

## getenv 
语法: 
```
   #include <stdlib.h>  
   char *getenv( const char *name ); 
```
功能： 函数返回环境变量name的值，非常依赖执行情况。如果无对应的环境变量name返回NULL。 

>相关主题:
system(). 

## longjmp 

语法: 
```
   #include <setjmp.h>  
   void longjmp( jmp_buf envbuf, int status ); 
```
功能： 函数使程序从前次对setjmp()的调用处继续执行。参数envbuf一般通过调用setjmp()设定。参数status 为setjmp()的返回值，用来指示不同地点longjmp()的执行. status 不能设定为零。 

>相关主题:
setjmp(). 


## qsort 

语法: 
```
   #include <stdlib.h>  
   void qsort( void *buf, size_t num, size_t size, int (*compare)(const void *, const void *) ); 
```

功能： 对buf 指向的数据(包含num 项,每项的大小为size)进行快速排序。如果函数compare 的第一个参数小于第二个参数，返回负值；如果等于返回零值；如果大于返回正值。函数对buf 指向的数据按升序排序。 

>相关主题:
bsearch(). 

## raise 

语法: 
```
   #include <signal.h>  
   int raise( int signal ); 
```
功能： 函数对程序发送指定的信号signal. 一些信号: 
|信号|含义|
|---|---|
|SIGABRT|终止错误|                 
|SIGFPE|浮点错误|
|SIGILL| 无效指令|
|SIGINT| 用户输入|
|SIGSEGV|非法内存存取|
|SIGTERM|终止程序|
 
返回零值为成功，非零为失败。 

>相关主题:
signal() 

## rand 
语法: 
```
   #include <stdlib.h>  
   int rand( void ); 
```
功能： 函数返回一个在零到RAND_MAX 之间的伪随机整数。例如：  
 ``` 
  srand( time(NULL) );    
  for( i = 0; i < 10; i++ )     
  printf( "Random number #%d: %d\n", i, rand() ); 
```

>相关主题:
srand() 


## setjmp 
语法: 
```
   #include <setjmp.h>  
   int setjmp( jmp_buf envbuf ); 
```
功能： 函数将系统栈保存于envbuf中，以供以后调用longjmp()。当第一次调用setjmp(),它的返回值为零。之后调用longjmp(),longjmp()的第二个参数即为setjmp()的返回值。是否有点疑问？请参阅longjmp(). 
>相关主题:
longjmp() 


## signal 

语法: 
```
   #include <signal.h>  
   void ( *signal( int signal, void (* func) (int)) ) (int); 
```   
功能： 当函数收到参数signal所表示的信号，参数func 所指向的函数即被调用。func 可以被定制为信号句柄或以下的宏(定义在signal.h中): 
|宏|解释|
|--|--|
|SIG_DFL|默认信号处理|
|SIG_IGN|忽略信号|
 
signal()返回先前为信号定义的函数地址，当错误发生返回SIG_ERR。 

## srand 
语法: 
```
   #include <stdlib.h>  
   void srand( unsigned seed ); 
```
功能： 设置rand()随机序列种子。对于给定的种子seed, rand()会反复产生特定的随机序列。     
```
srand( time(NULL) );    
for( i = 0; i < 10; i++ )      
printf( "Random number #%d: %d\n", i, rand() ); 
```
>相关主题:
rand(), time(). 


## system 
语法: 
```
   #include <stdlib.h>  
   int system( const char *command );
```    
功能： 函数返回给定的命令字符串command 进行系统调用。如果命令执行正确通常返回零值。如果command 为 NULL, system()将尝试是否有可用的命令解释器。 如果有返回非零值，否则返回零值。 

>相关主题:
exit(), 


## va_arg 

语法: 
```
   #include <stdarg.h>  
   type va_arg( va_list argptr, type ); 
   void va_end( va_list argptr );  
   void va_start( va_list argptr, last_parm ); 
```   
功能： 宏va_arg()用于给函数传递可变长度的参数列表。 
首先，必须调用va_start() 传递有效的参数列表va_list和函数强制的第一个参数。第一个参数代表将要传递的参数的个数。 
其次，调用va_arg()传递参数列表va_list 和将被返回的参数的类型。va_arg()的返回值是当前的参数。 
再次，对所有的参数重复调用va_arg() 
最后，调用va_end()传递va_list对完成后的清除是必须的。 
For example: 
```
    int sum( int, ... );
    int main( void ) {
      int answer = sum( 4, 4, 3, 2, 1 );
      printf( "The answer is %d\n", answer );
      return( 0 );
    }

    int sum( int num, ... ) {
      int answer = 0;
      va_list argptr;
      va_start( argptr, num );
      for( ; num > 0; num-- )
        answer += va_arg( argptr, int );
      va_end( argptr );
      return( answer );
    }
```
这段代码显示10,他们是4+3+2+1。 