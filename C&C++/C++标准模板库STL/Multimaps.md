# Multimaps 


## begin 
语法:
``` 
  iterator begin();
```
 

begin()函数返回一个迭代器，指向multimap的第一个元素。




## clear 
语法:
``` 
  void clear();
```
 

clear()函数删除multimap中的所有元素。




## count 
语法: 
```
  size_type count( const key_type &key );
```
 

count()函数返回multimap中键值等于key的元素的个数。




## empty 
语法: 
```
  bool empty();
```
 

empty()函数返回真(true)如果multimap为空，否则返回假(false)。




## end 
语法: 
```
  iterator end();
```
 

end()函数返回一个迭代器，指向multimap的尾部。




## equal_range 
语法:
``` 
  pair equal_range( const key_type &key );
```
 

equal_range()函数查找multimap中键值等于key的所有元素，返回指示范围的两个迭代器。




## erase 
语法: 
```
  void erase( iterator pos );
  void erase( iterator start, iterator end );
  size_type erase( const key_type &key );
```
 

erase()函数删除在pos位置的元素，或者删除在start和end之间的元素，或者删除那些值为key的所有元素。




## find 
语法: 
```
  iterator find( const key_type &key );
```
 

find()函数返回一个迭代器指向键值为key的元素，如果没找到就返回指向multimap尾部的迭代器。




## get_allocator 
语法:
``` 
  allocator_type get_allocator();
```
 

get_allocator()函数返回multimap的配置器。




## insert 
语法: 
```
  iterator insert( iterator pos, const TYPE &val );
  void insert( input_iterator start, input_iterator end );
  pair insert( const TYPE &val );
```
 

insert()函数： 

- 插入val到pos的后面，然后返回一个指向这个元素的迭代器。 
- 插入start到end的元素到multimap中。 
- 只有在val不存在时插入val。返回值是一个指向被插入元素的迭代- 器和一个描述是否插入的bool值。 



## key_comp 
语法:
``` 
  key_compare key_comp();
```
 

key_comp()函数返回一个比较key的函数。




## lower_bound 
语法:
``` 
  iterator lower_bound( const key_type &key );
```
 

lower_bound()函数返回一个迭代器，指向multimap中键值>=key的第一个元素。




## max_size 
语法:
``` 
  size_type max_size();
```
 

max_size()函数返回multimap能够保存的最大元素个数。




## rbegin 
语法: 
```
  reverse_iterator rbegin();
```
 

rbegin()函数返回一个指向multimap尾部的逆向迭代器。




## rend 
语法: 
```
  reverse_iterator rend();
```
 

rend()函数返回一个指向multimap头部的逆向迭代器。




## size 
语法: 
```
  size_type size();
```
 

size()函数返回multimap中保存的元素个数。




## swap 
语法: 
```
  void swap( multimap &obj );
```
 

swap()交换obj和现mulitmap中的元素。




## upper_bound 
语法:
``` 
  iterator upper_bound( const key_type &key );
```
 

upper_bound()函数返回一个迭代器，指向multimap中键值>key的第一个元素。




## value_comp 
语法:
``` 
  value_compare value_comp();
```
 

value_comp()函数返回一个比较元素value的函数。
