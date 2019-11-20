# 标准C内存函数

## calloc 
语法: 

``` 
  #include <stdlib.h>
  void *calloc( size_t num, size_t size );
``` 

功能： 函数返回一个指向num 数组空间，每一数组元素的大小为size。如果错误发生返回NULL。 

>相关主题:
free(), malloc(), and realloc(). 

## free 

语法: 

``` 
  #include <stdlib.h>
  void free( void *ptr );
``` 

功能： 函数释放指针ptr指向的空间，以供以后使用。指针ptr 必须由先前对malloc(), calloc(), realloc()的调用返回。例如: 
```
    typedef struct data_type {
      int age;
      char name[20];
    } data;
    
    data *willy;
    willy = (data*) malloc( sizeof(willy) );
    ...
    free( willy );
```
>相关主题:
calloc(), malloc(), and realloc(). 


## malloc 

语法: 

``` 
  #include <stdlib.h>
  void *malloc( size_t size );
``` 

功能： 函数指向一个大小为size的空间，如果错误发生返回NULL。 存储空间的指针必须为堆，不能是栈。这样以便以后用free函数释放空间。例如: 
```
    typedef struct data_type {
      int age;
      char name[20];
    } data;
    
    data *bob;
    bob = (data*) malloc( sizeof(data) );
    if( bob != NULL ) {
      bob->age = 22;
      strcpy( bob->name, "Robert" );
      printf( "%s is %d years old\n", bob->name, bob->age );
    }
    free( bob );
```

>相关主题:
free(), realloc(), and calloc(). 

## realloc 

语法: 

``` 
  #include <stdlib.h>
  void *realloc( void *ptr, size_t size );
``` 

功能： 函数将ptr 对象的储存空间改变为给定的大小size。 参数size可以是任意大小，大于或小于原尺寸都可以。 返回值是指向新空间的指针，如果错误发生返回NULL。 

>相关主题:
free(), malloc(), and calloc().
