# C++I/O


## 构造器
语法:
``` 
  fstream( const char *filename, openmode mode );
  ifstream( const char *filename, openmode mode );
  ofstream( const char *filename, openmode mode );
```
 

Tstream, ifstream, 和ofstream对象用于文件输入/输出. 可选择模式通过使用ios stream mode flags定义了一个文件如何打开。filename 指定被打开的文件并与流相关联。例如，下面的代码读取输入的数据并追加结果到一个输出文件中. 
```
    ifstream fin( "/tmp/data.txt" );
    ofstream fout( "/tmp/results.txt", ios::app );
    while( fin >> temp ) 
      fout << temp + 2 << endl;
    fin.close();
    fout.close();
```
输入和输出文件流可以相似的方式被使用在C++预定义I/O流，cin 和 cout. 

>相关主题:
close(), open() 


## bad 
语法:
``` 
  bool bad();
```
 

如果当前的流发生致命的错误，bad()函数返回true，否则返回false。 

>相关主题:
good() 


## clear 
语法:
``` 
  void clear( iostate flags = goodbit );
```
 

函数clear()清除与当前流相关联的标志。默认标志是goodbit它清除所有标志.否则只有指定的标志被清除。 

>相关主题:
rdstate() 


## close 
语法:
``` 
  void close();
```
 

Tclose()函数关闭相关的文件流。 

>相关主题:
open() 


## eof 
语法: 
```
  bool eof();
```
 

如果到达相关联的输入文件的末尾，eof()函数返回true，否则返回false。例如： 
```
    char ch;
    ifstream fin( "temp.txt" );
    while( !fin.eof() ) {
      fin >> ch;
      cout << ch;
    }
    fin.close();
```

>相关主题:
bad(), fail(), good(), rdstate(), clear() 


## fail 
语法:
``` 
  bool fail();
```
 

如果当前流发生错误fail()函数返回true ，否则返回false 。

>相关主题:
good(), eof(), bad(), clear(), rdstate() 


## fill 
语法:
``` 
  char fill();
  char fill( char ch );
```
 

函数fill()可以返回当前填充字符，或者设置当前填充字符为ch 。填充字符被定义为用来填充字符，当一个数字比较指定宽度T小时。默认的填充字符是空格。 

>相关主题:
precision(), width() 


## flags 
语法:
``` 
  fmtflags flags();
  fmtflags flags( fmtflags f );
```
 

flags()函数或者返回当前流的格式标志，或者为当前流设置标志为f。

>相关主题:
unsetf(), setf() 


## flush 
语法:
``` 
  ostream &flush();
```
 

flush()函数可以引起当把前流的缓冲区写出到附属设备中去。这个函数对于打印调试信息很用处，因为当程序有机会把缓冲区内容写出到屏幕之前，程序会被中断。灵活地使用flush()可以保证你所有的调试状态都实在的打印出来。 

>相关主题:
put(), write() 


## gcount 
语法:
``` 
  streamsize gcount();
```
 

函数gcount()被用于输入流，并返回上一次输入操作被读入的字符的数目。 

>相关主题:
get(), getline(), read() 


## get 
语法:
``` 
  int get();
  istream &get( char &ch );
  istream &get( char *buffer, streamsize num );
  istream &get( char *buffer, streamsize num, char delim );
  istream &get( streambuf &buffer );
  istream &get( streambuf &buffer, char delim );
```
 

get()函数被用于输入流，和以下这些: 

- 读入一个字符并返回它的值， 
- 读入一个字符并把它存储在ch， 
- 读取字符到buffer直到num - 1个字符被读入, 或者碰到EOF或换行标志， 
- 读取字符到buffer直到已读入num - 1 个字符，或者碰到EOF或delim(delim直到下一次不会被读取)，
- 读取字符到buffer中，直到碰到换行或EOF， 
- 或是读取字符到buffer中，直到碰到换行，EOF或delim。(相反, delim直到下一个get()不会被读取 ). 

例如，下面的代码一个字符一个字符的显示文件temp.txt中的内容： 
```
    char ch;
    ifstream fin( "temp.txt" );
    while( fin.get(ch) )
      cout << ch; 
    fin.close();
```
>相关主题:
put(), read(), getline() 


## getline 
语法:
``` 
  istream &getline( char *buffer, streamsize num );
  istream &getline( char *buffer, streamsize num, char delim );
```
 

getline()函数用于输入流，读取字符到buffer中，直到下列情况发生： 

- num - 1个字符已经读入, 
- 碰到一个换行标志，
- 碰到一个EOF， 
- 或者，任意地读入，直到读到字符delim。delim字符不会被放入buffer中。 

>相关主题:
get(), read() 


## good 
语法:
``` 
  bool good();
```
 

如果当前流没有发生错误，函数good()返回true ，否则返回false。 

>相关主题:
bad(), fail(), eof(), clear(), rdstate() 


## ignore 
语法:
``` 
  istream &ignore( streamsize num=1, int delim=EOF );
```
 

ignore()函数用于输入流。它读入字符，直到已经读了num 个字符(默认为1)或是直到字符delim 被读入(默认为EOF). 

>相关主题:
get(), getline() 


## open 
语法:
``` 
  void open( const char *filename );
  void open( const char *filename, openmode mode );
```
 

函数open()用于文件流。它打开filename 并将其与当前的流相关联。可以选择的模式有： 

|模式 |含义|
|---|---| 
|ios::app| 添加输出 
|ios::ate| 当已打开时寻找到EOF 
|ios::binary| 以二进制模式打开文件 
|ios::in |为读取打开文件 
|ios::out |为写入打开文件 
|ios::trunc| 覆盖存在的文件 

如果open()失败，当用于一个布尔表达式中时，作为结果的流会给出对错误的评估。例如： 
```
  ifstream inputStream("file.txt");
  if( !inputStream ) {
    cerr << "Error opening input stream" << endl;
    return;
  }
```

>相关主题:
close(), fstream(), ifstream(), ofstream(), 


## peek 
语法:
``` 
  int peek();
```
 

函数peek()用于输入流中，并返回在流中的下一个字符或如果是处于被入的文件的结尾处返回EOF。peek()不会把字符从流中移除。 

>相关主题:
get(), putback() 


## precision 
语法:
``` 
  streamsize precision();
  streamsize precision( streamsize p );
```
 

precision()函数设置或返回当前要被显示的浮点变量的位数。例如，下面的代码： 
```
    float num = 314.15926535;
    cout.precision( 5 );
    cout << num;
```
displays 
```
    314.16
```

>相关主题:
width(), fill() 


## put 
语法:
``` 
  ostream &put( char ch );
```
 

函数put()用于输出流，并把字符ch写入流中。 

>相关主题:
write(), get() 


## putback 
语法:
``` 
  istream &putback( char ch );
```
 

putback()函数用于输入流，并且返回以前读的字符ch到输入流中。 

>相关主题:
peek() 


## rdstate 
语法:
``` 
  iostate rdstate();
```
 

rdstate()函数返回当前流的状态。iostate 对象有下面这些标志： 

|标志 |含义 |
|badbit |发生致命的错误 
|eofbit |已经发现EOF 
|failbit| 一个非致命性错误已经发生 
|goodbit| 没有发生错误 

>相关主题:
eof(), good(), bad(), clear(), fail() 




## read 
语法:
``` 
  istream &read( char *buffer, streamsize num );
```
 

函数read()用于输入流，在将字符放入buffer 之前从流中读取num 个字节。如果碰到EOF，read()中止，丢弃不论多少个字节已经放入。例如： 
```
    struct {
      int height;
      int width;
    } rectangle;
    
    input_file.read( (char *)(&rectangle), sizeof(rectangle) );
    if( input_file.bad() ) {
      cerr << "Error reading data" << endl;
      exit( 0 );
    }
```

>相关主题:
gcount(), get(), getline(), write() 


## seekg 
语法:
``` 
  istream &seekg( off_type offset, ios::seekdir origin );
  istream &seekg( pos_type position );
```
 

函数seekg()用于输入流，并且它将重新设置"get"指针到当前流的从origin偏移offset个字节的位置上，或是置"get"指针在position位置。 

>相关主题:
seekp(), tellg(), tellp() 


## seekp 
语法:
``` 
  ostream &seekp( off_type offset, ios::seekdir origin );
  ostream &seekp( pos_type position );
```
 

seekp()函数用于输出流，但在其它方面和seekg()很类似。

>相关主题:
seekg(), tellg(), tellp() 


## setf 
语法: 
```
  fmtflags setf( fmtflags flags );
  fmtflags setf( fmtflags flags, fmtflags needed );
```
 

函数setf()设置当前流的格式化标志为flags。可选标志needed 只允许flags标志和needed标志都被设置。返回值是前面设置的标志。

例如： 
```
    int number = 0x3FF;
    cout.setf( ios::dec );
    cout << "Decimal: " << number << endl;
    cout.unsetf( ios::dec );
    cout.setf( ios::hex );
    cout << "Hexadecimal: " << number << endl;
```

提示，上面的代码和下面的代码的功能是一致的: 
```
    int number = 0x3FF;
    cout << "Decimal: " << number << endl << hex << "Hexadecimal: " << number << dec << endl;
```

参考 manipulators. 

>相关主题:
flags(), unsetf() 


## sync_with_stdio 
语法:
``` 
  static bool sync_with_stdio( bool sync=true );
```
 

sync_with_stdio()函数有打开或关闭使用C++风格I/O系统混合C风格的I/O系统的功能。 




## tellg 
语法:
``` 
  pos_type tellg();
```
 

tellg()函数用于输入流，并返回流中"get"指针的当前位置。 

>相关主题:
seekg(), seekp(), tellp() 


## tellp 
语法:
``` 
  pos_type tellp();
```
 

tellp()函数用于输出流中，并返回在流中当前"put"指针的位置。 例如，下面的代码显示了当一个文件指针写入一个流的时候的情形： 
```
  string s("In Xanadu did Kubla Khan...");

  ofstream fout("output.txt");

  for( int i=0; i < s.length(); i++ ) {
    cout << "File pointer: " << fout.tellp();
    fout.put( s[i] );
    cout << " " << s[i] << endl;
  }

  fout.close();
```

>相关主题:
seekg(), seekp(), tellg() 


## unsetf 
语法:
``` 
  void unsetf( fmtflags flags );
```
 

函数unsetf()用于清除与当前流相关的给定的标志flags。什么标志呢? 

>相关主题:
setf(), flags() 


## width 
语法:
``` 
  int width();
  int width( int w );
```
 

函数 width()返回当前的宽度。可选择参数w用于设定宽度大小。宽度是指每一次输出中显示的字符的最小数目。例如： 
```
    cout.width( 5 );
    cout << "2";
```
displays 
```
        2
```
(在一个'2'的后面紧跟着四个空格) 

>相关主题:
precision(), fill() 


## write 
语法:
``` 
  ostream &write( const char *buffer, streamsize num );
```
 

write()函数用于输出流，从buffer中写num个字节到当前输出流中。 

>相关主题:
read(), put() 