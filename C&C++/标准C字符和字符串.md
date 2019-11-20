## 标准c字符和字符串



## atof
语法:
```
  #include <stdlib.h>
  double atof( const char *str );
```

功能:将字符串str转换成一个双精度数值并返回结果。 参数str 必须以有效数字开头,但是允许以“E”或“e”除外的任意非数字字符结尾。例如：
```
    x = atof( "42.0is_the_answer" );
```
x的值为42.0.

>相关主题:
atoi() and atol().




## atoi

语法:
```
  #include <stdlib.h>
  int atoi( const char *str );
 ```

功能：将字符串str转换成一个整数并返回结果。参数str 以数字开头，当函数从str 中读到非数字字符则结束转换并将结果返回。例如，
```
    i = atoi( "512.035" );
```
i 的值为 512.

>相关主题:
atof() and atol().




## atol

语法:
```
  #include <stdlib.h>
  long atol( const char *str );
```

功能：将字符串转换成长整型数并返回结果。函数会扫描参数str字符串，跳过前面的空格字符，直到遇上数字或正负符号才开始做转换，而再遇到非数字或字符串结束时才结束转换，并将结果返回。例如，
```
    x = atol( "1024.0001" );
```
x的值为1024L.

>相关主题:
atof() and atoi().




## isalnum

语法:
```
  #include <ctype.h>
  int isalnum( int ch );
```
功能：如果参数是数字或字母字符，函数返回非零值，否则返回零值。
```
    char c;
    scanf( "%c", &c );
    if( isalnum(c) )
      printf( "You entered the alphanumeric character %c\n", c );
```
>相关主题:
isalpha(), iscntrl(), isdigit(), isgraph(), isprint(), ispunct(), and isspace().




## isalpha

语法:
```
  #include <ctype.h>
  int isalpha( int ch );
```

功能：如果参数是字母字符，函数返回非零值，否则返回零值。
```
    char c;
    scanf( "%c", &c );
    if( isalpha(c) )
      printf( "You entered a letter of the alphabet\n" );
```

>相关主题:
isalnum(), iscntrl(), isdigit(), isgraph(), isprint(), ispunct(), and isspace().




## iscntrl

语法:
```
  #include <ctype.h>
  int iscntrl( int ch );
```

功能：如果参数是控制字符（0和0x1F之间的字符，或者等于0x7F）函数返回非零值，否则返回零值。 

>相关主题:
isalnum(), isalpha(), isdigit(), isgraph(), isprint(), ispunct(), and isspace().




## isdigit

语法:
```
  #include <ctype.h>
  int isdigit( int ch );
```

功能：如果参数是0到9之间的数字字符，函数返回非零值，否则返回零值.
```
    char c;
    scanf( "%c", &c );
    if( isdigit(c) )
      printf( "You entered the digit %c\n", c );
```

>相关主题:
isalnum(), isalpha(), iscntrl(), isgraph(), isprint(), ispunct(), and isspace().




## isgraph

语法:
```
  #include <ctype.h>
  int isgraph( int ch );
```

功能：如果参数是除空格外的可打印字符（可见的字符），函数返回非零值，否则返回零值。

>相关主题:
isalnum(), isalpha(), iscntrl(), isdigit(), isprint(), ispunct(), and isspace().




## islower

语法:
```
  #include <ctype.h>
  int islower( int ch );
```
功能：如果参数是小写字母字符，函数返回非零值，否则返回零值。

>相关主题:
isupper()




## isprint

语法:
```
  #include <ctype.h>
  int isprint( int ch );
``` 

功能：如果参数是可打印字符（包括空格），函数返回非零值，否则返回零值。

>相关主题:
isalnum(), isalpha(), iscntrl(), isdigit(), isgraph(), ispunct(), and isspace().




## ispunct

语法:
```
  #include <ctype.h>
  int ispunct( int ch );
``` 

功能：如果参数是除字母，数字和空格外可打印字符，函数返回非零值，否则返回零值。

>相关主题:
isalnum(), isalpha(), iscntrl(), isdigit(), isgraph(), isprint(), and isspace().




## isspace

语法:
```
  #include <ctype.h>
  int isspace( int ch );
``` 

功能：如果参数是空格类字符（即：单空格，制表符，垂直制表符，满页符，回车符，新行符），函数返回非零值，否则返回零值。

>相关主题:
isalnum(), isalpha(), iscntrl(), isdigit(), isgraph(), and ispunct().




## isupper

语法:
```
  #include <ctype.h>
  int isupper( int ch );
``` 

功能：如果参数是大写字母字符，函数返回非零值，否则返回零值。

>相关主题:
tolower()




## isxdigit

语法:
```
  #include <ctype.h>
  int isxdigit( int ch );
``` 

功能：如果参数是十六进制数字字符（即：A-F, a-f, 0-9），函数返回非零值，否则返回零值。

>相关主题:
isalnum(), isalpha(), iscntrl(), isdigit(), isgraph(), ispunct(), and isspace().




## memchr

语法:
```
  #include <string.h>
  void *memchr( const void *buffer, int ch, size_t count );
```

功能：函数在buffer指向的数组的count个字符的字符串里查找ch 首次出现的位置。返回一个指针，指向ch 在字符串中首次出现的位置, 如果ch 没有在字符串中找到，返回NULL。例如:
```
    char names[] = "Alan Bob Chris X Dave";
    if( memchr(names,'X',strlen(names)) == NULL )
      printf( "Didn't find an X\n" );
    else
      printf( "Found an X\n" );
```
>相关主题:
memcpy() and strstr().




## memcmp

语法:
```
  #include <string.h>
  int memcmp( const void *buffer1, const void *buffer2, size_t count );
```

功能：函数比较buffer1 和 buffer2的前count 个字符。返回值如下:

|返回值|  解释| 
|---|---|
|less than 0| buffer1 is less than buffer2| 
|equal to 0| buffer1 is equal to buffer2| 
|greater than 0 |buffer1 is greater than buffer2| 


>相关主题:
memchr(), memcpy(), and strcmp().




## memcpy

语法:
```
  #include <string.h>
  void *memcpy( void *to, const void *from, size_t count );
``` 

功能：函数从from中复制count 个字符到to中，并返回to指针。 如果to 和 from 重叠，则函数行为不确定。

>相关主题:
memmove().




## memmove

语法:
```
  #include <string.h>
  void *memmove( void *to, const void *from, size_t count );
``` 

功能: 与mencpy相同，不同的是当to 和 from 重叠，函数正常仍能工作。

>相关主题:
memcpy().




## memset

语法:
```
  #include <string.h>
  void *memset( void *buffer, int ch, size_t count );
``` 

功能: 函数拷贝ch 到buffer 从头开始的count 个字符里, 并返回buffer指针。 memset() 可以应用在将一段内存初始化为某个值。例如：
```
    memset( the_array, '\0', sizeof(the_array) );
```
这是将一个数组的所以分量设置成零的很便捷的方法。

>相关主题:
memcmp(), memcpy(), and memmove().




## strcat

语法:
```
  #include <string.h>
  char *strcat( char *str1, const char *str2 );
``` 

功能：函数将字符串str2 连接到str1的末端，并返回指针str1. 例如：
```
    printf( "Enter your name: " );
    scanf( "%s", name );
    title = strcat( name, " the Great" );
    printf( "Hello, %s\n", title );
```
>相关主题:
strchr(), strcmp(), and strcpy().




## strchr
语法:
```
  #include <string.h>
  char *strchr( const char *str, int ch );
``` 

功能：函数返回一个指向str 中ch 首次出现的位置，当没有在str 中找ch到返回NULL。

>相关主题:
strpbrk(), strspn(), strstr(), and strtok().




## strcmp

语法:
```
  #include <string.h>
  int strcmp( const char *str1, const char *str2 );
``` 

功能：比较字符串str1 and str2, 返回值如下:

|返回值|  解释| 
|---|---|
|less than 0| str1 is less than str2| 
|equal to 0| str1 is equal to str2| 
|greater than 0 |str1 is greater than str2| 

例如:
```
    printf( "Enter your name: " );
    scanf( "%s", name );
    if( strcmp( name, "Mary" ) == 0 )
      printf( "Hello, Dr. Mary!\n" );
```
相关主题:
memcmp(), strchr(), strcpy(), and strncmp().




## strcoll

语法:
```
  #include <string.h>
  int strcoll( const char *str1, const char *str2 );
```

功能：比较字符串str1 和 str2, 很象strcmp. 但是, strcoll() 使用在目前环境中由setlocale()设定的次序进行比较。




## strcpy

语法:
```
  #include <string.h>
  char *strcpy( char *to, const char *from );
``` 

功能：复制字符串from 中的字符到字符串to，包括空值结束符。返回值为指针to。

>相关主题:
memcpy(), strchr(), strcmp(), strncmp(), and strncpy().




## strcspn

语法:
```
  #include <string.h>
  size_t strcspn( const char *str1, const char *str2 );
``` 

功能：函数返回str1 开头连续n个字符都不含字符串str2内字符的字符数。

>相关主题:
strrchr(), strpbrk(), strstr(), and strtok().




## strerror

语法:
```
  #include <string.h>
  char *strerror( int num );
``` 

功能：函数返回一个被定义的与某错误代码相关的错误信息。




## strlen

语法:
```
  #include <string.h>
  size_t strlen( char *str );
``` 

功能：函数返回字符串str 的长度( 即空值结束符之前字符数目)。

>相关主题:
memcpy(), strchr(), strcmp(), and strncmp().




## strncat

语法:
```
  #include <string.h>
  char *strncat( char *str1, const char *str2, size_t count );
``` 

功能：将字符串from 中至多count个字符连接到字符串to中，追加空值结束符。返回处理完成的字符串。

>相关主题:
strcat(), strnchr(), strncmp(), and strncpy().




## strncmp

语法:
```
  #include <string.h>
  int strncmp( const char *str1, const char *str2, size_t count );
``` 

功能：比较字符串str1 和 str2中至多count个字符。返回值如下：

|返回值|  解释 |
 |---|---|
|less than 0| str1 is less than str2| 
|equal to 0 |str1 is equal to str2| 
|greater than 0| str1 is greater than str2| 
 

如果参数中任一字符串长度小于count, 那么当比较到第一个空值结束符时，就结束处理。

>相关主题:
strcmp(), strnchr(), and strncpy().




## strncpy

语法:
```
  #include <string.h>
  char *strncpy( char *to, const char *from, size_t count );
``` 

功能：将字符串from 中至多count个字符复制到字符串to中。如果字符串from 的长度小于count，其余部分用'\0'填补。返回处理完成的字符串。

>相关主题:
memcpy(), strchr(), strncat(), and strncmp().




## strpbrk

语法:
```
  #include <string.h>
  char *strpbrk( const char *str1, const char *str2 );
``` 

功能：函数返回一个指针，它指向字符串str2中任意字符在字符串str1 首次出现的位置，如果不存在返回NULL。

>相关主题:
strspn(), strrchr(), strstr(), and strtok().




## strrchr

语法:
```
  #include <string.h>
  char *strrchr( const char *str, int ch );
``` 

功能：函数返回一个指针，它指向字符ch 在字符串str末次出现的位置，如果匹配失败，返回NULL。

>相关主题:
strpbrk(), strspn(), strstr(), strtok(),




## strspn

语法:
```
  #include <string.h>
  size_t strspn( const char *str1, const char *str2 );
``` 

功能：函数返回字符串str1中第一个不包含于字符串str2的字符的索引。

>相关主题:
strpbrk(), strrchr(), strstr(), strtok(),




## strstr

语法:
```
  #include <string.h>
  char *strstr( const char *str1, const char *str2 );
``` 

功能：函数返回一个指针，它指向字符串str2 首次出现于字符串str1中的位置，如果没有找到，返回NULL。

>相关主题:
strchr(), strcspn(), strpbrk(), strspn(), strtok(), strrchr(),




## strtod

语法:
```
  #include <stdlib.h>
  double strtod( const char *start, char **end );
``` 

功能：函数返回带符号的字符串start所表示的浮点型数。字符串end 指向所表示的浮点型数之后的部分。如果溢出发生，返回HUGE_VAL或 -HUGE_VAL。

>相关主题:
atof()




## strtok

语法:
```
  #include <string.h>
  char *strtok( char *str1, const char *str2 );
``` 

功能：函数返回字符串str1中紧接“标记”的部分的指针, 字符串str2是作为标记的分隔符。如果分隔标记没有找到，函数返回NULL。为了将字符串转换成标记，第一次调用str1 指向作为标记的分隔符。之后所以的调用str1 都应为NULL。

例如:
```
    char str[] = "now # is the time for all # good men to come to the # aid of their country";
    char delims[] = "#";
    char *result = NULL;
    result = strtok( str, delims );
    while( result != NULL ) {
        printf( "result is \"%s\"\n", result );
         result = strtok( NULL, delims );
    }
```
以上代码的运行结果是：
```
    result is "now "
    result is " is the time for all "
    result is " good men to come to the "
    result is " aid of their country"
```
>相关主题:
strchr(), strcspn(), strpbrk(), strrchr(), and strspn().




## strtol

语法:
```
  #include <stdlib.h>
  long strtol( const char *start, char **end, int base );
```  

功能：函数返回带符号的字符串start所表示的长整型数。参数base代表采用的进制方式。指针end 指向start所表示的整型数之后的部分。如果返回值无法用长整型表示，函数则返回LONG_MAX或LONG_MIN. 错误发生时，返回零。

>相关主题:
atol().




## strtoul

语法:
```
  #include <stdlib.h>
  unsigned long strtoul( const char *start, char **end, int base );
``` 

功能：函数基本等同 strtol(), 不同的是，它不仅可以返回长整型数，而且可以返回无符号的长整型数。

>相关主题:
strtol()




## strxfrm

语法:
```
  #include <string.h>
  size_t strxfrm( char *str1, const char *str2, size_t num );
``` 

功能：函数将字符串str2 的前num 个字符存储到字符串str1中。如果strcoll() 处理字符串str1 和旧的字符串str2, 返回值和strcmp()的处理结果一样。

>相关主题:
strcmp(), strcoll(),




## tolower

语法:
```
  #include <ctype.h>
  int tolower( int ch );
``` 

功能：函数字符ch的小写形式。

>相关主题:
toupper(),




## toupper

语法:
```
  #include <ctype.h>
  int toupper( int ch );
``` 

功能：函数字符ch的大写形式。

>相关主题:
tolower(),
