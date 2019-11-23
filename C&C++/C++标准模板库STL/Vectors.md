# Vectors


## 构造函数
语法:
``` 
  vector();
  vector( size_type num, const TYPE &val );
  vector( const vector &from );
  vector( input_iterator start, input_iterator end );
```
 

C++ Vectors可以使用以下任意一种参数方式构造: 

- 无参数 - 构造一个空的vector, 
- 数量(num)和值(val) - 构造一个初始放入num个值为val的元素的Vector 
- vector(from) - 构造一个与vector from 相同的vector 
- 迭代器(start)和迭代器(end) - 构造一个初始值为[start,end)区间元素的Vector(注:半开区间). 

举例,下面这个实例构造了一个包含5个值为42的元素的Vector
```
vector<int> v1( 5, 42 );
```




## 运算符
语法:
``` 
  v1 == v2
  v1 != v2
  v1 <= v2
  v1 >= v2
  v1 < v2
  v1 > v2 
  v[]
```
 

C++ Vectors能够使用标准运算符: ==, !=, <=, >=, <, 和 >. 要访问vector中的某特定位置的元素可以使用 [] 操作符. 

两个vectors被认为是相等的,如果: 

- 它们具有相同的容量 
- 所有相同位置的元素相等. 

vectors之间大小的比较是按照词典规则. 

>相关内容: at(). 


## assign函数 
语法:
``` 
  void assign( input_iterator start, input_iterator end );
  void assign( size_type num, const TYPE &val );
```
 

assign() 函数要么将区间[start, end)的元素赋到当前vector,或者赋num个值为val的元素到vector中.这个函数将会清除掉为vector赋值以前的内容.

 




## at函数 
语法:
``` 
  TYPE at( size_type loc );
```
 

at() 函数 返回当前Vector指定位置loc的元素的引用. at() 函数 比 [] 运算符更加安全, 因为它不会让你去访问到Vector内越界的元素. 例如, 考虑下面的代码:
```
vector<int> v( 5, 1 );

for( int i = 0; i < 10; i++ ) {
  cout << "Element " << i << " is " << v[i] << endl;
}
  
```

这段代码访问了vector末尾以后的元素,这将可能导致很危险的结果.以下的代码将更加安全: 
```
vector<int> v( 5, 1 );

for( int i = 0; i < 10; i++ ) {
  cout << "Element " << i << " is " << v.at(i) << endl;
}
```  
取代试图访问内存里非法值的作法,at() 函数能够辨别出访问是否越界并在越界的时候抛出一个异常.

>相关内容: [] 操作符 




## back 函数 
语法:
``` 
  TYPE back();
```
 

back() 函数返回当前vector最末一个元素的引用.例如: 
```
vector<int> v;

for( int i = 0; i < 5; i++ ) {
  v.push_back(i);
}

cout << "The first element is " << v.front() 
     << " and the last element is " << v.back() << endl;
```  
这段代码产生如下结果:
```
The first element is 0 and the last element is 4
```

>相关内容: front(). 


## begin 函数 
语法:
``` 
  iterator begin();
```
 

begin()函数返回一个指向当前vector起始元素的迭代器.例如,下面这段使用了一个迭代器来显示出vector中的所有元素:
```
vector<int> v1( 5, 789 );
vector<int>::iterator it;
for( it = v1.begin(); it != v1.end(); it++ )
  cout << *it << endl;
```
>相关内容: end(). 


## capacity 函数 
语法:
``` 
  size_type capacity();
```
 

capacity() 函数 返回当前vector在重新进行内存分配以前所能容纳的元素数量.




## clear 函数 
语法:
``` 
  void clear();
```
 

clear()函数删除当前vector中的所有元素.




## empty 函数 
语法:
``` 
  bool empty();
```
 

如果当前vector没有容纳任何元素,则empty()函数返回true,否则返回false.例如,以下代码清空一个vector,并按照逆序显示所有的元素:
```
vector<int> v;
  
for( int i = 0; i < 5; i++ ) {
    v.push_back(i);
  }
  
while( !v.empty() ) {
    cout << v.back() << endl;
    v.pop_back();
  }
```

>相关内容: size() 


## end 函数 
语法:
``` 
  iterator end();
```
 

end() 函数返回一个指向当前vector末尾元素的下一位置的迭代器.注意,如果你要访问末尾元素,需要先将此迭代器自减1.

>相关内容: begin() 




## erase 函数 
语法:
``` 
  iterator erase( iterator loc );
  iterator erase( iterator start, iterator end );
```
 

erase函数要么删作指定位置loc的元素,要么删除区间[start, end)的所有元素.返回值是指向删除的最后一个元素的下一位置的迭代器.例如:
```
// 创建一个vector,置入字母表的前十个字符
vector<char> alphaVector;
for( int i=0; i < 10; i++ )
    alphaVector.push_back( i + 65 );
int size = alphaVector.size();

vector<char>::iterator startIterator;
vector<char>::iterator tempIterator;

for( int i=0; i < size; i++ )
{
    tartIterator = alphaVector.begin();
    alphaVector.erase( startIterator );

    // Display the vector
    for( tempIterator = alphaVector.begin(); tempIterator != alphaVector.end(); tempIterator++ )
    cout << *tempIterator;
    cout << endl;
} 
```
这段代码将会显示如下输出: 
```
BCDEFGHIJ
CDEFGHIJ
DEFGHIJ
EFGHIJ
FGHIJ
GHIJ
HIJ
IJ
J
```

>相关内容: pop_back(). 


## front 函数 
语法:
``` 
  TYPE front();
```
 

front()函数返回当前vector起始元素的引用

>相关内容: back(). 




## get_allocator 函数 
语法:
``` 
  allocator_type get_allocator();
```
 

get_allocator() 函数返回当前vector的内存分配器. 




## insert 函数 
语法:
``` 
  iterator insert( iterator loc, const TYPE &val );
  void insert( iterator loc, size_type num, const TYPE &val );
  void insert( iterator loc, input_iterator start, input_iterator end );
```
 

insert() 函数有以下三种用法: 

- 在指定位置loc前插入值为val的元素,返回指向这个元素的迭代器, 
- 在指定位置loc前插入num个值为val的元素 
- 在指定位置loc前插入区间[start, end)的所有元素 . 

举例: 
```
//创建一个vector,置入字母表的前十个字符
vector<char> alphaVector;
for( int i=0; i < 10; i++ )
  alphaVector.push_back( i + 65 );

//插入四个C到vector中
vector<char>::iterator theIterator = alphaVector.begin();
alphaVector.insert( theIterator, 4, 'C' );

//显示vector的内容
for( theIterator = alphaVector.begin(); theIterator != alphaVector.end(); theIterator++ )
  cout << *theIterator;
```
这段代码将显示: 
```
CCCCABCDEFGHIJ
```



## max_size 函数 
语法:
``` 
  size_type max_size();
```
 

max_size() 函数返回当前vector所能容纳元素数量的最大值(译注:包括可重新分配内存). 




## pop_back 
语法:
``` 
  void pop_back();
```
 

pop_back()函数删除当前vector最末的一个元素,例如: 
```
vector<char> alphaVector;
for( int i=0; i < 10; i++ )
    alphaVector.push_back( i + 65 );

int size = alphaVector.size();
vector<char>::iterator theIterator;
for( int i=0; i < size; i++ ) {
  alphaVector.pop_back();
  for( theIterator = alphaVector.begin(); theIterator != alphaVector.end(); theIterator++ )
      cout << *theIterator;
  cout << endl;
}
```
这段代码将显示以下输出: 
```
ABCDEFGHI
ABCDEFGH
ABCDEFG
ABCDEF
ABCDE
ABCD
ABC
AB
A
```

>相关内容: erase(). 


## push_back 函数 
语法:
``` 
  void push_back( const TYPE &val );
```
 

push_back()添加值为val的元素到当前vector末尾




## rbegin 函数 
语法:
``` 
  reverse_iterator rbegin();
```
 

rbegin函数返回指向当前vector末尾的逆迭代器.(译注:实际指向末尾的下一位置,而其内容为末尾元素的值,详见逆代器相关内容)




## rend 函数 
语法: 
```
  reverse_iterator rend();
```
 

rend()函数返回指向当前vector起始位置的逆迭代器. 




## reserve 函数 
语法:
``` 
  void reserve( size_type size );
```
 

reserve()函数为当前vector预留至少共容纳size个元素的空间.(译注:实际空间可能大于size)




## resize 函数 
语法:
``` 
  void resize( size_type size, TYPE val );
```
 

resize() 函数改变当前vector的大小为size,且对新创建的元素赋值val




## size 函数 
语法: 
```
  size_type size();
```
 

size() 函数返回当前vector所容纳元素的数目 

>相关内容: empty() 




## swap 函数 
语法:
``` 
  void swap( vector &from );
```
 

swap()函数交换当前vector与vector from的元素
