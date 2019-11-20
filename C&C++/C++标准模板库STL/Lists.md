# Lists

## 赋值(assign) 
语法:
``` 
  void assign( input_iterator start, input_iterator end );
  void assign( size_type num, const TYPE &val );
```
 

assign()函数以迭代器start和end指示的范围为list赋值或者为list赋值num个以val为值的元素。

>相关主题:
insert(), 


## back 
语法:
``` 
  reference back();
```
 

back()函数返回一个引用，指向list的最后一个元素。 

>相关主题:
front(), pop_back(), 


## begin 
语法:
``` 
  iterator begin();
```
 

begin()函数返回一个迭代器，指向list的第一个元素。例如， 
```
    // 创建一个元素类型是字符的链表
    list<char> charList;
    for( int i=0; i < 10; i++ )
      charList.push_front( i + 65 );

    // 显示这个链表
    list<char>::iterator theIterator;
    for( theIterator = charList.begin(); theIterator != charList.end(); theIterator++ )
      cout << *theIterator;
```

>相关主题:
end(), 


## clear 
语法:
``` 
  void clear();
```
 

clear()函数删除list的所有元素。




## empty 
语法:
``` 
  bool empty();
```
 

empty()函数返回真(true)如果链表为空，否则返回假。例如：
```
    list<int> the_list;
    for( int i = 0; i < 10; i++ )
      the_list.push_back( i );  
    while( !the_list.empty() ) {
      cout << the_list.front() << endl;
      the_list.pop_front();
    }
``` 
    




## end 
语法:
``` 
  iterator end();
```
 

end()函数返回一个迭代器，指向链表的末尾。

>相关主题:
begin(), 


## erase 
语法:
``` 
  iterator erase( iterator pos );
  iterator erase( iterator start, iterator end );
```
 

erase()函数删除以pos指示位置的元素, 或者删除start和end之间的元素。 返回值是一个迭代器，指向最后一个被删除元素的下一个元素。




## front 
语法:
``` 
  reference front();
```
 

front()函数返回一个引用，指向链表的第一个元素。
```
    list<int> the_list;
    for( int i = 0; i < 10; i++ )
      the_list.push_back( i );  
    while( !the_list.empty() ) {
      cout << the_list.front() << endl;
      the_list.pop_front();
    }
```
>相关主题:
back(), 


## get_allocator 
语法:
``` 
  allocator_type get_allocator();
```
 

get_allocator()函数返回链表的配置器。




## insert 
语法:
``` 
  iterator insert( iterator pos, const TYPE &val );
  void insert( iterator pos, size_type num, const TYPE &val );
  void insert( iterator pos, input_iterator start, input_iterator end );
```
 

insert()插入元素val到位置pos，或者插入num个元素val到pos之前，或者插入start到end之间的元素到pos的位置。返回值是一个迭代器，指向被插入的元素。 




## max_size 
语法:
``` 
  size_type max_size();
```
 

max_size()函数返回链表能够储存的元素数目。




## merge 
语法:
``` 
  void merge( list &lst );
  void merge( list &lst, Comp compfunction );
```
 

merge()函数把自己和lst链表连接在一起，产生一个整齐排列的组合链表。如果指定compfunction，则将指定函数作为比较的依据。




## pop_back 
语法:
``` 
  void pop_back();
```
 

pop_back()函数删除链表的最后一个元素。

>相关主题:
pop_front(), 


## pop_front 
语法:
``` 
  void pop_front();
```
 

pop_front()函数删除链表的第一个元素。

>相关主题:
pop_back(), 


## push_back 
语法:
``` 
  void push_back( const TYPE &val );
```
 

push_back()将val连接到链表的最后。例如：
```
    list<int> the_list;
    for( int i = 0; i < 10; i++ )
      the_list.push_back( i );
```
>相关主题:
push_front(), 


## push_front 
语法:
``` 
  void push_front( const TYPE &val );
```
 

push_front()函数将val连接到链表的头部。

>相关主题:
push_back(), 


## rbegin 
语法:
``` 
  reverse_iterator rbegin();
```
 

rbegin()函数返回一个逆向迭代器，指向链表的末尾。

>相关主题:
rend(), 


## remove 
语法: 
```
  void remove( const TYPE &val );
```
 

remove()函数删除链表中所有值为val的元素。例如 
```
    // 创建一个链表，元素是字母表的前10个元素
    list<char> charList;
    for( int i=0; i < 10; i++ )
      charList.push_front( i + 65 );

    // 删除所有'E'的实例
    charList.remove( 'E' );
```




## remove_if 
语法:
``` 
  void remove_if( UnPred pr );
```
 

remove_if()以一元谓词pr为判断元素的依据，遍历整个链表。如果pr返回true则删除该元素。




## rend 
语法: 
```
  reverse_iterator rend();
```
 

rend()函数迭代器指向链表的头部。




## resize 

语法:
``` 
  void resize( size_type num, TYPE val );
```
 

resize()函数把list的大小改变到num。被加入的多余的元素都被赋值为val




## reverse 
语法:
``` 
  void reverse();
```
 

reverse()函数把list所有元素倒转。




## size 
语法: 
```
  size_type size();
```
 

size()函数返回list中元素的数量。




## 排序(sort) 

语法:
```
  void sort();
  void sort( Comp compfunction );
```
 

sort()函数为链表排序，默认是升序。如果指定compfunction的话，就采用指定函数来判定两个元素的大小。




## splice 
语法:
```  
  void splice( iterator pos, list &lst );
  void splice( iterator pos, list &lst, iterator del );
  void splice( iterator pos, list &lst, iterator start, iterator end );
``` 
 

splice()函数把lst连接到pos的位置。如果指定其他参数，则插入lst中del所指元素到现链表的pos上，或者用start和end指定范围。 




## swap 
语法:
``` 
  void swap( list &lst );
```
 

swap()函数交换lst和现链表中的元素。


## unique 
语法: 
``` 
  void unique();
  void unique( BinPred pr );
``` 
 

unique()函数删除链表中所有重复的元素。如果指定pr，则使用pr来判定是否删除。
