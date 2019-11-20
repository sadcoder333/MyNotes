# Double-Ended Queues

## Constructors 

语法:   
```
  deque();
  deque( size_type size );
  deque( size_type num, const TYPE &val );
  deque( const deque &from );
  deque( input_iterator start, input_iterator end );
```
 

C++ Deques能用以下方式创建: 

- 无参，创建一个空双向队列 
- size - 创建一个大小为size的双向队列 
- num and val - 放置num个val的拷贝到队列中， 
- from - 从from创建一个内容一样的双向队列 
- start 和 end - 创建一个队列，保存从start到end的元素。 

例如，下列代码创建并显示一个双向队列： 
```
  // 创建一个双向队列，里面有10个1
  deque dq( 10, 1 );
  // 创建一个迭代器
  deque::iterator iter;

  // 显示这个双向队列
  for( iter = dq.begin(); iter != dq.end(); iter++ ){ 
    cout << *iter << endl;
  }
```


## Operators 
语法:
``` 
  []
```
你可以使用[]操作符访问双向队列中单个的元素。


## assign 
语法:
``` 
  void assign( input_iterator start, input_iterator end);
  void assign( Size num, const TYPE &val );
```
assign()函数用start和end指示的范围为双向队列赋值，或者设置成num个val。


## at 
语法:
``` 
  reference at( size_type pos );
```
at()函数返回一个引用，指向双向队列中位置pos上的元素。


## back 
语法:
``` 
  reference back();
```
 
back()返回一个引用，指向双向队列中最后一个元素。


## begin 
语法:
``` 
  iterator begin();
```
begin()函数返回一个迭代器，指向双向队列的第一个元素。


## clear 
语法: 
```
  void clear();
```
clear()函数删除双向队列中所有元素。

## empty 

语法:
``` 
  bool empty();
```
empty()返回真如果双向队列为空，否则返回假。

## end 

语法: 
```
  iterator end();
```
end()函数返回一个迭代器，指向双向队列的尾部。

## erase 

语法: 
```
  iterator erase( iterator pos );
  iterator erase( iterator start, iterator end );
```
erase()函数删除pos位置上的元素，或者删除start和end之间的所有元素。返回值是一个iterator，指向被删除元素的后一个元素。


## front 

语法: 
```
  reference front();
```
front()函数返回一个引用，指向双向队列的头部。

## get_allocator 

语法:
``` 
  allocator_type get_allocator();
```
get_allocator()函数返回双向队列的配置器。


## insert 

语法:
``` 
  iterator insert( iterator pos, size_type num, const TYPE &val );
  void insert( iterator pos, input_iterator start, input_iterator end );
```
insert()在pos前插入num个val值，或者插入从start到end范围内的元素到pos前面。


## max_size 
语法:
``` 
  size_type max_size();
```
 

max_size()返回双向队列能容纳的最大元素个数。


## pop_back 
语法:
``` 
  void pop_back();
```
pop_back()删除双向队列尾部的元素。


## pop_front 
语法:
``` 
  void pop_front();
```
 
pop_front()删除双向队列头部的元素。


## push_back 
语法:
``` 
  void push_back( const TYPE &val );
```
 

push_back()函数在双向队列的尾部加入一个值为val的元素。


## push_front 
语法: 
```
  void push_front( const TYPE &val );
```

push_front()函数在双向队列的头部加入一个值为val的元素。



## rbegin 
语法:
``` 
  reverse_iterator rbegin();
```
 
rbegin()返回一个指向双向队列尾部的逆向迭代器。


## rend 
语法:
``` 
  reverse_iterator rend();
```

rend()返回一个指向双向队列头部的逆向迭代器。


## resize 

语法: 
```
  void resize( size_type num, TYPE val );
```
 
resize()改变双向队列的大小为num，另加入的元素都被填充为val。


## size

语法:
``` 
  size_type size();
```
 
size()函数返回双向队列中的元素个数。


## swap

语法: 
```
  void swap( deque &target );
```
 
swap()函数交换target和现双向队列中元素。
