# Bitsets 

## Constructors 

语法: 
```
  bitset();
  bitset( unsigned long val );
```
 

C++ Bitsets能以无参的形式创建，或者提供一个长无符号整数，它将被转化为二进制，然后插入到bitset中。当创建bitset时，模板中提供的数字决定bitset有多长。

例如，以下代码创建两个bitsets，然后显示它们： 
```
  // 创建一个8位长的bitset
  bitset<8> bs;

  // 显示这个bitset
  for( int i = (int) bs.size(); i >= 0; i-- ) {
    cout << bs[i] << " ";
  }
  cout << endl;

  // 创建另一个bitset
  bitset<8> bs2( (long) 131 );

  // 显示
  for( int i = (int) bs2.size(); i >= 0; i-- ) {
    cout << bs2[i] << " ";
  }
  cout << endl;
```



## Operators 

语法: 
```
  !=, ==, &=, ^=, |=, ~, <<=, >>=, []
```
 

这些操作符都可以和bitsets一起工作。它们被这样定义: 

|符号|含义|
|--|--|
|!= |返回真如果两个bitset不相等。| 
|== |返回真如果两个bitset相等。 |
|&= |完成两个bitset间的与运算。 |
|^= |完成两个bitset间的异或运算。 |
|\|=| 完成两个 |
|~| 反置bitset (和调用 flip()类似)| 
|<<=| 把bitset向左移动 |
|>>=| 把bitset向右移动 |
|[x] |返回第x个位的引用| 

例如，以下代码创建一个bitset，然后向左移动4个位：
```
  // 创建一个bitset
  bitset<8> bs2( (long) 131 );

  cout << "bs2 is " << bs2 << endl;

  // 向左移动4位
  bs2 <<= 4;

  cout << "now bs2 is " << bs2 << endl;
```

当上述代码运行时，显示：
```
  bs2 is 10000011
  now bs2 is 00110000
```

## any 

语法: 
```
  bool any();
```
any()函数返回真如果有位被设置为1，否则返回假。

## count 

语法: 
```
  size_type count();
```
 
count()函数bitset中被设置成1的位的个数。

## flip 

语法: 
```
  bitset &flip();
  bitset &flip( size_t pos );
```

flip()函数反置bitset中所有的位，即将1设为0，0设为1。如果指定pos，那么只有pos上的位被反置。

>相关主题:
~ operator 
--------------------------------------------------------------------------------

## none 

语法: 
```
  bool none();
```

none()返回真如果没有位被设为1，否则返回假。

## reset 

语法: 
```
  bitset &reset();
  bitset &reset( size_t pos );
```
reset()重置bitset（全部设为0），如果指定pos，那么只有pos上的位被重置。

## set 

语法: 
```
  bitset &set();
  bitset &set( size_t pos, int val=1 );
```
 
set()函数设置bitset上所有的位，然后返回bitset。如果指定pos，那么只有pos上的位被设置。



## size 
语法:
``` 
  size_t size();
```
size()返回bitset能容纳的位。

## test 
语法:
``` 
  bool test( size_t pos );
```

test()函数返回在pos上的位的值。



## to_string 
语法: 
```
  string to_string();
```

to_string()函数返回bitset的字符串形式。



## to_ulong 
语法:
``` 
  unsigned long to_ulong();
```
 
to_ulong()返回bitset的无符号长整数形式。
