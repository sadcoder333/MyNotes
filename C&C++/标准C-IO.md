# 标准C-I/O

## clearerr 
语法:
``` 
  #include <stdio.h>
  void clearerr( FILE *stream );
```

clearerr函数重置错误标记和给出的流的EOF指针. 当发生错误时,你可以使用perror()判断实际上发生了何种错误. 

>相关主题:
feof(), ferror(), 和perror(). 

## fclose 

语法:
``` 
  #include <stdio.h>
  int fclose( FILE *stream );
```
 

函数fclose()关闭给出的文件流, 释放已关联到流的所有缓冲区. fclose()执行成功时返回0,否则返回EOF. 

>相关主题:
fopen(), freopen(), 和fflush(). 

## feof 

语法:
``` 
  #include <stdio.h>
  int feof( FILE *stream );
```
 

函数feof()在到达给出的文件流的文件尾时返回一个非零值. 

>相关主题:
clearerr(), ferror(), perror(), putc()和 getc(). 

## ferror 

语法: 
```
  #include <stdio.h>
  int ferror( FILE *stream );
```
 

ferror()函数检查stream(流)中的错误, 如果没发生错误返回0,否则返回非零. 如果发生错误, 使用perror()检测发生什么错误. 

>相关主题:
clearerr(), feof(), perror(), 


## fflush 
语法:
``` 
  #include <stdio.h>
  int fflush( FILE *stream );
```
 

如果给出的文件流是一个输出流,那么fflush()把输出到缓冲区的内容写入文件. 如果给出的文件流是输入类型的,那么fflush()会清除输入缓冲区. fflush()在调试时很实用,特别是对于在程序中输出到屏幕前发生错误片段时. 直接调用 fflush( STDOUT )输出可以保证你的调试输出可以在正确的时间输出. 
```
    printf( "Before first call\n" );
    fflush( STDOUT );
    shady_function();
    printf( "Before second call\n" );
    fflush( STDOUT );
    dangerous_dereference();
```
>相关主题:
fclose(), fopen(), fread(), fwrite(), getc(), 和putc(). 


## fgetc 
语法:
``` 
  #include <stdio.h>
  int fgetc( FILE *stream );
```
 

fgetc()函数返回来自stream(流)中的下一个字符,如果到达文件尾或者发生错误时返回EOF. 

>相关主题:
fputc(), getc(), putc(), 和fopen(). 


## fgetpos 
语法:
``` 
  #include <stdio.h>
  int fgetpos( FILE *stream, fpos_t *position );
```
 

fgetpos()函数保存给出的文件流(stream)的位置指针到给出的位置变量(position)中. position变量是fpos_t类型的(它在stdio.h中定义)并且是可以控制在FILE中每个可能的位置对象. fgetpos()执行成功时返回0,失败时返回一个非零值. 

>相关主题:
fsetpos(), fseek()和 ftell(). 


## fgets 

语法:
``` 
  #include <stdio.h>
  char *fgets( char *str, int num, FILE *stream );
```
 

函数fgets()从给出的文件流中读取[num - 1]个字符并且把它们转储到str(字符串)中. fgets()在到达行末时停止,在这种情况下,str(字符串)将会被一个新行符结束. 如果fgets()达到[num - 1]个字符或者遇到EOF, str(字符串)将会以null结束.fgets()成功时返回str(字符串),失败时返回NULL. 




## fopen 

语法: 
```
  #include <stdio.h>
  FILE *fopen( const char *fname, const char *mode );
```

 

fopen()函数打开由fname(文件名)指定的文件, 并返回一个关联该文件的流.如果发生错误, fopen()返回NULL. mode(方式)是用于决定文件的用途(例如 用于输入,输出,等等) 

|Mode(方式) |意义|
|---|----| 
|"r" |打开一个用于读取的文本文件| 
|"w" |创建一个用于写入的文本文件 |
|"a" |附加到一个文本文件 |
|"rb" |打开一个用于读取的二进制文件| 
|"wb" |创建一个用于写入的二进制文件 |
|"ab" |附加到一个二进制文件 |
|"r+" |打开一个用于读/写的文本文件| 
|"w+" |创建一个用于读/写的文本文件 |
|"a+" |打开一个用于读/写的文本文件 |
|"rb+" |打开一个用于读/写的二进制文件| 
|"wb+" |创建一个用于读/写的二进制文件 |
|"ab+"| 打开一个用于读/写的二进制文件 |

示例: 
```
    char ch;
    FILE *input = fopen( "stuff", "r" );
    ch = getc( input );
``` 




## fprintf 
语法:
``` 
  #include <stdio.h>
  int fprintf( FILE *stream, const char *format, ... );
```
 

fprintf()函数根据指定的format(格式)(格式)发送信息(参数)到由stream(流)指定的文件. fprintf()只能和printf()一样工作. fprintf()的返回值是输出的字符数,发生错误时返回一个负值. 

示例: 
```
    char name[20] = "Mary";
    FILE *out;
    out = fopen( "output.txt", "w" );
    if( out != NULL )
      fprintf( out, "Hello %s\n", name );
```
>相关主题:
printf() 和fscanf(). 


## fputc 
语法:
``` 
  #include <stdio.h>
  int fputc( int ch, FILE *stream );
```
 

函数fputc()把给出的字符ch写到给出的输出流. 返回值是字符, 发生错误时返回值是EOF. 

>相关主题:
fgetc(), fopen(), fprintf(), fread(), 和fwrite(). 


## fputs 
语法:
``` 
  #include <stdio.h>
  int fputs( const char *str, FILE *stream );
```
 

fputs()函数把str(字符串)指向的字符写到给出的输出流. 成功时返回非负值, 失败时返回EOF. 

>相关主题:
fgets(), gets(), puts(), fprintf(), 和fscanf(). 


## fread 
语法:
``` 
  #include <stdio.h>
  int fread( void *buffer, size_t size, size_t num, FILE *stream );
```
 

函数fread()读取[num]个对象(每个对象大小为size(大小)指定的字节数),并把它们替换到由buffer(缓冲区)指定的数组. 数据来自给出的输入流. 函数的返回值是读取的内容数量... 

使用feof()或ferror()判断到底发生哪个错误. 

>相关主题:
fwrite(), fopen(),fscanf(), fgetc()和getc(). 


## freopen 
语法:
``` 
  #include <stdio.h>
  FILE *freopen( const char *fname, const char *mode, FILE *stream );
```
 

freopen()函数常用于再分配一个以存在的流给一个不同的文件和方式(mode).在调用本函数后,给出的文件流将会用mode(方式)指定的访问模式引用fname(文件名). freopen()的返回值是新的文件流,发生错误时返回NULL. 

>相关主题:
fopen() 和fclose(). 


## fscanf 

语法:
``` 
  #include <stdio.h>
  int fscanf( FILE *stream, const char *format, ... );
```
 

函数fscanf()以scanf()的执行方式从给出的文件流中读取数据. fscanf()的返回值是事实上已赋值的变量的数,如果未进行任何分配时返回EOF. 

>相关主题:
scanf() 和fprintf(). 


## fseek 

语法: 
```
  #include <stdio.h>
  int fseek( FILE *stream, long offset, int origin );
```
 

函数fseek()为给出的流设置位置数据. origin的值应该是下列值其中之一(在stdio.h中定义): 

|名称| 说明| 
|---|---|
|SEEK_SET |从文件的开始处开始搜索 |
|SEEK_CUR |从当前位置开始搜索 |
|SEEK_END| 从文件的结束处开始搜索| 


fseek()成功时返回0,失败时返回非零. 你可以使用fseek()移动超过一个文件,但是不能在开始处之前. 使用fseek()清除关联到流的EOF标记. 

>相关主题:
ftell(), rewind(), fopen(), fgetpos()和 fsetpos(). 


## fsetpos 
语法:
``` 
  #include <stdio.h>
  int fsetpos( FILE *stream, const fpos_t *position );
```
 

fsetpos()函数把给出的流的位置指针移到由position对象指定的位置. fpos_t是在stdio.h中定义的. fsetpos()执行成功返回0,失败时返回非零. 

>相关主题:
fgetpos(), fseek()和 ftell(). 


## ftell 
语法: 
```
  #include <stdio.h>
  long ftell( FILE *stream );
```
 

ftell()函数返回stream(流)当前的文件位置,如果发生错误返回-1. 

>相关主题:
fseek()和 fgetpos(). 


## fwrite 
语法:
``` 
  #include <stdio.h>
  int fwrite( const void *buffer, size_t size, size_t count, FILE *stream );
```
 

fwrite()函数从数组buffer(缓冲区)中, 写count个大小为size(大小)的对象到stream(流)指定的流. 返回值是已写的对象的数量. 

>相关主题:
fread(), fscanf(), getc()和 fgetc(). 


## getc 
语法:
``` 
  #include <stdio.h>
  int getc( FILE *stream );
```
 

getc()函数从stream(流)获取并返回下一个字符,如果到达文件尾返回EOF. getc()和fgetc()是一样的. 例如: 
```
    char ch;
    FILE *input = fopen( "stuff", "r" );
    
    ch = getc( input );
    while( ch != EOF ) {
      printf( "%c", ch );
      ch = getc( input );
    }
```
>相关主题:
fputc(), fgetc(), putc()和 fopen(). 


## getchar 

语法:
``` 
  #include <stdio.h>
  int getchar( void );
```
 

getchar()函数从STDIN(标准输入)获取并返回下一个字符,如果到达文件尾返回EOF. 

>相关主题:
fputc(), fgetc(), putc()和 fopen(). 


## gets 

语法:
``` 
  #include <stdio.h>
  char *gets( char *str );
```
 

gets()函数从STDIN(标准输入)读取字符并把它们加载到str(字符串)里,直到遇到新行(\n)或到达EOF. 新行字符翻译为一个null中断符. gets()的返回值是读入的字符串,如果错误返回NULL. 

>相关主题:
fputs(), fgetc(),fgets()和 puts(). 


## perror 

语法: 
```
  #include <stdio.h>
  void perror( const char *str );
```
 

perror()函数打印str(字符串)和一个相应的执行定义的错误消息到全局变量errno中. 




## printf 

语法:
``` 
  #include <stdio.h>
  int printf( const char *format, ... );
```
 

printf()函数根据format(格式)给出的格式打印输出到STDOUT(标准输出)和其它参数中. 

字符串format(格式)由两类项目组成 - 显示到屏幕上的字符和定义printf()显示的其它参数. 基本上, 你可以指定一个包含文本在内的format(格式)字符串,也可以是映射到printf()其它参数的"特殊"字符. 例如本代码 
```
    char name[20] = "Bob";
    int age = 21;
    printf( "Hello %s, you are %d years old\n", name, age );
```
显示下列输出: 
```
    Hello Bob, you are 21 years old
```
%s 表示, "在这里插入首个参数,一个字符串." %d 表示第二个参数(一个整数)应该放置在那里. 不同的"%-codes"表示不同的变量类型, 也可以限制变量的长度. 

|Code| 格式|
|--|--| 
| %c|  字符 | 
| %d | 带符号整数 | 
| %i | 带符号整数 | 
| %e | 科学计数法, 使用小写"e" | 
| %E | 科学计数法, 使用大写"E" | 
| %f | 浮点数 | 
| %g | 使用%e或%f中较短的一个 | 
| %G | 使用%E或%f中较短的一个 | 
| %o | 八进制 | 
| %s | 一串字符 | 
| %u | 无符号整数 | 
| %x | 无符号十六进制数, 用小写字母 | 
| %X|  无符号十六进制数, 用大写字母 | 
| %p | 一个指针 | 
| %n|  参数应该是一个指向一个整数的指针，指向的是字符数放置的位置| 
|%%| 一个'%'符号 |

一个位于一个%和格式化命令间的整数担当着一个最小字段宽度说明符,并且加上足够多的空格或0使输出足够长. 如果你想填充0,在最小字段宽度说明符前放置0. 你可以使用一个精度修饰符,它可以根据使用的格式代码而有不同的含义. 

用%e, %E和 %f,精度修饰符让你指定想要的小数位数. 例如, 
```
    %12.6f
```
将会至少显示12位数字,并带有6位小数的浮点数. 

用%g和 %G, 精度修饰符决定显示的有效数的位数最大值. 

用%s,精度修饰符简单的表示一个最大的最大长度, 以补充句点前的最小字段长度. 

所有的printf()的输出都是右对齐的,除非你在%符号后放置了负号. 例如, 
```
    %-12.4f
```
将会显示12位字符,4位小数位的浮点数并且左对齐. 你可以修改带字母l和h%d, %i, %o, %u和 %x 等类型说明符指定长型和短型数据类型 (例如 %hd 表示一个短整数). %e, %f和 %g 类型说明符,可以在它们前面放置l指出跟随的是一个double. %g, %f和 %e 类型说明符可以置于字符'#'前保证出现小数点, 即使没有小数位. 带%x类型说明符的'#'字符的使用, 表示显示十六进制数时应该带'0x'前缀. 带%o类型说明符的'#'字符的使用, 表示显示八进制数时应该带一个'0'前缀. 

你可以在输出字符串中包含 连续的Escape序列. 

printf()的返回值是打印的字符数,如果发生错误则返回一个负值. 

>相关主题:
scanf()和 fprintf(). 


## putc 

语法:
``` 
  #include <stdio.h>
  int putc( int ch, FILE *stream );
```
 

putc()函数把字符ch写到stream(流)中. 返回值是写入的字符, 发生错误时返回EOF. 例如: 
```
    char ch;
    FILE *input;
    input = fopen( "temp.cpp", "r" );
    ch = getc( input );
    while( ch != EOF ) {
      printf( "%c", ch );
      ch = getc( input );
    }
```
显示"temp.cpp"的内容到屏幕. 

>相关主题:
fgetc(), fputc(), getchar()和 putchar(). 


## putchar 

语法:
``` 
  #include <stdio.h>
  int putchar( int ch );
```
 

putchar()函数把ch写到STDOUT(标准输出). 代码 
```
    putchar( ch );
```
和 
```
    putc( ch, STDOUT );
```
一样. 
putchar()的返回值是被写的字符, 发生错误时返回EOF. 

>相关主题:
putc() 


## puts 

语法: 
```
  #include <stdio.h>
  int puts( char *str );
```
 

函数puts()把str(字符串)写到STDOUT(标准输出)上. puts() 成功时返回非负值, 失败时返回EOF. 

>相关主题:
putc(), gets()和 printf(). 


## remove 

语法: 
```
  #include <stdio.h>
  int remove( const char *fname );
```
 

remove()函数删除由fname(文件名)指定的文件. remove()成功时返回0,如果发生错误返回非零. 

>相关主题:
rename() 


## rename 

语法: 
```
  #include <stdio.h>
  int rename( const char *oldfname, const char *newfname );
```
 

函数rename()更改文件oldfname的名称为newfname. rename()成功时返回0,错误时返回非零. 

>相关主题:
remove() 


## rewind 

语法: 
```
  #include <stdio.h>
  void rewind( FILE *stream );
```
 

函数rewind()把文件指针移到由stream(流)指定的开始处, 同时清除和流相关的错误和EOF标记. 

>相关主题:
fseek() 


## scanf 

语法: 
```
  #include <stdio.h>
  int scanf( const char *format, ... );
```
 

scanf()函数根据由format(格式)指定的格式从stdin(标准输入)读取,并保存数据到其它参数. 它和printf()有点类似. format(格式)字符串由控制字符,空白字符和非空白字符组成. 控制字符以一个%符号开始,如下: 


|控制字符 |说明|
|---|---| 
|%c| 一个单一的字符 |
|%d| 一个十进制整数 |
|%i| 一个整数 |
|%e, %f, %g| 一个浮点数 |
|%o| 一个八进制数 |
|%s| 一个字符串 |
|%x| 一个十六进制数 |
|%p |一个指针 |
|%n |一个等于读取字符数量的整数 |
|%u |一个无符号整数 |
|%[] |一个字符集 |
|%% |一个精度符号 |

scanf()读取匹配format(格式)字符串的输入. 当读取到一个控制字符, 它把值放置到下一个变量. 空白(tabs, 空格等等)会跳过. 非空白字符和输入匹配, 然后丢弃. 如果是一个在%符号和控制符间的数量, 那么只有指定数量的字符转换到变量中. 如果scanf()遇到一个字符集(用%[]控制字符表示), 那么在括号中的任意字符都会读取到变量中. scanf()的返回值是成功赋值的变量数量, 发生错误时返回EOF. 

>相关主题:
printf()和 fscanf(). 


## setbuf 

语法: 
```
  #include <stdio.h>
  void setbuf( FILE *stream, char *buffer );
```
 

setbuf()函数设置stream(流)使用buffer(缓冲区),如果buffer(缓冲区)是null,关闭缓冲. 如果使用非标准缓冲尺寸, 它应该由BUFSIZ字符决定长度. 

>相关主题:
fopen(), fclose(), setvbuf(), 


## setvbuf 

语法: 
```
  #include <stdio.h>
  int setvbuf( FILE *stream, char *buffer, int mode, size_t size );
```
 

函数setvbuf()设置用于stream(流)的缓冲区到buffer(缓冲区),其大小为size(大小). mode(方式)可以是: 

- _IOFBF, 表示完全缓冲 
- _IOLBF, 表示线缓冲 
- _IONBF, 表示无缓存 

>相关主题:
setbuf(), 


## sprintf 

语法: 
```
  #include <stdio.h>
  int sprintf( char *buffer, const char *format, ... );
```
 

sprintf()函数和printf()类似, 只是把输出发送到buffer(缓冲区)中.返回值是写入的字符数量. 例如: 
```
    char string[50];
    int file_number = 0;
    
    sprintf( string, "file.%d", file_number );
    file_number++;
    output_file = fopen( string, "w" );
```
>相关主题:
printf(), fsprintf(), 


## sscanf 

语法: 
```
  #include <stdio.h>
  int sscanf( const char *buffer, const char *format, ... );
```
 

函数sscanf()和scanf()类似, 只是输入从buffer(缓冲区)中读取. 

>相关主题:
scanf(), fscanf(), 


## tmpfile 

语法: 
```
  #include <stdio.h>
  FILE *tmpfile( void );
```
 

函数tempfile()用一个独特的文件名打开一个临时文件,并返回一个到该文件的指针.如果发生错误则返回null. 

>相关主题:
tmpnam(), 


## tmpnam 

语法: 
```
  #include <stdio.h>
  char *tmpnam( char *name );
```
 
tmpnam()函数创建一个独特的文件名并保存在name中. tmpnam()最多可以调用TMP_MAX指定的次数. 

>相关主题:
tmpfile(), 


## ungetc 

语法: 
```
  #include <stdio.h>
  int ungetc( int ch, FILE *stream );
```
 

函数ungetc()把字符ch放回到stream(流)中. 

>相关主题:
getc(), 


## vprintf, vfprintf和 vsprintf 

语法: 
```
  #include <stdarg.h>
  #include <stdio.h>
  int vprintf( char *format, va_list arg_ptr );
  int vfprintf( FILE *stream, const char *format, va_list arg_ptr );
  int vsprintf( char *buffer, char *format, va_list arg_ptr );
```
 

这些函数和printf()非常相似, fprintf()和 sprintf()的不同在于参数列表是一个指向一系列参数的指针. va_list在STDARG.H中定义,并且也可以被va_arg()使用. 例如: 
```
    void error( char *fmt, ... ) {
      va_list args;
      
      va_start( args, fmt );
      fprintf( stderr, "Error: " );
      vfprintf( stderr, fmt, args );
      fprintf( stderr, "\n" );
      va_end( args );
      exit( 1 );
    }
```
