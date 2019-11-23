# Maps 



## begin 
语法:
``` 
  iterator begin();
```
 

begin()函数返回一个迭代器指向map的第一个元素。




## clear 
语法:
``` 
  void clear();
```
 

clear()函数删除map中的所有元素。




## count 
语法:
``` 
  size_type count( const KEY_TYPE &key );
```
 

count()函数返回map中键值等于key的元素的个数。




## empty 
语法: 
```
  bool empty();
```
 

empty()函数返回真(true)如果map为空，否则返回假(false)。




## end 
语法: 
```
  iterator end();
```
 

end()函数返回一个迭代器指向map的尾部。




## equal_range 
语法:
``` 
  pair equal_range( const KEY_TYPE &key );
```
 

equal_range()函数返回两个迭代器——一个指向第一个键值为key的元素，另一个指向最后一个键值为key的元素。




## erase 
语法:
``` 
  void erase( iterator pos );
  void erase( iterator start, iterator end );
  size_type erase( const KEY_TYPE &key );
```
 

erase()函数删除在pos位置的元素，或者删除在start和end之间的元素，或者删除那些值为key的所有元素。




## find 
语法: 
```
  iterator find( const KEY_TYPE &key );
```
 

find()函数返回一个迭代器指向键值为key的元素，如果没找到就返回指向map尾部的迭代器。




## get_allocator 
语法:
``` 
  allocator_type get_allocator();
```
 

get_allocator()函数返回map的配置器。




## insert 
语法: 
```
  iterator insert( iterator pos, const pair<KEY_TYPE,VALUE_TYPE> &val );
  void insert( input_iterator start, input_iterator end );
  pair<iterator, bool> insert( const pair<KEY_TYPE,VALUE_TYPE> &val );
```
 

insert()函数： 

- 插入val到pos的后面，然后返回一个指向这个元素的迭代器。 
- 插入start到end的元素到map中。 
- 只有在val不存在时插入val。返回值是一个指向被插入元素的迭代器和一个描述是否插入的bool值。 




## key_comp 
语法:
``` 
  key_compare key_comp();
```
 

key_comp()函数返回一个比较key的函数。




## lower_bound 
语法:
``` 
  iterator lower_bound( const KEY_TYPE &key );
```
 

lower_bound()函数返回一个迭代器，指向map中键值>=key的第一个元素。




## max_size 
语法:
``` 
  size_type max_size();
```
 

max_size()函数返回map能够保存的最大元素个数。




## rbegin 
语法:
``` 
  reverse_iterator rbegin();
```
 

rbegin()函数返回一个指向map尾部的逆向迭代器。




## rend 
语法: 
```
  reverse_iterator rend();
```
 

rend()函数返回一个指向map头部的逆向迭代器。




## size 
语法: 
```
  size_type size();
```
 

size()函数返回map中保存的元素个数。




## swap 
语法: 
```
  void swap( map &obj );
```
 

swap()交换obj和现map中的元素。




## upper_bound 
语法:
``` 
  iterator upper_bound( const KEY_TYPE &key );
```
 

upper_bound()函数返回一个迭代器，指向map中键值>key的第一个元素。




## value_comp 
语法:
``` 
  value_compare value_comp();
```
 

value_comp()函数返回一个比较元素value的函数。
