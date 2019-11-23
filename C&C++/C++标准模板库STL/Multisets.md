# Multisets


## begin

语法: 

 
```
iterator begin();
```


返回指向当前集合中第一个元素的迭代器。





## clear

语法: 

 
```
void clear();
```


清除当前集合中的所有元素。





## count

语法: 

 
```
size_type count( const key_type &key );
```


返回当前集合中出现的某个值的元素的数目。





## empty

语法: 

 
```
bool empty();
```


如果当前多元集合为空，返回true；否则返回false。





## end

语法: 

 
```
iterator end();
``` 


返回指向当前集合中最后一个元素的迭代器。





## equal_range

语法: 

 
```
pair equal_range( const key_type &key );
``` 


返回集合中与给定值相等的上下限的两个迭代器。





## erase

语法: 

 
```
void erase( iterator pos );
void erase( iterator start, iterator end );
size_type erase( const key_type &key );
``` 


说明：

- 删除i元素；
- 删除从start开始到end结束的元素；
- 删除等于key值的所有元素（返回被删除的元素的个数）。





## find

语法:


 
```
iterator find( const key_type &key );
``` 


在当前集合中查找等于key值的元素，并返回指向该元素的迭代器；如果没有找到，返回指向多元集合最后一个元素的迭代器。





## get_allocator

语法: 

 
```
allocator_type get_allocator();
``` 


返回当前集合的分配器。





## insert

语法: 

 
```
iterator insert( iterator pos, const TYPE &val );
void insert( input_iterator start, input_iterator end );
pair insert( const TYPE &val );
``` 


insert():

- 在迭代器i前插入val，并返回一个指向该元素的迭代器；
- 将迭代器start开始到end结束返回内的元素插入到集合中；
- 在当前集合中插入val元素，并返回指向该元素的迭代器和一个布尔值来说明val是否成功的被插入了。





## key_comp

语法: 

 
```
key_compare key_comp();
``` 


返回一个用于元素间值比较的函数对象。





## lower_bound

语法: 

 
```
iterator lower_bound( const key_type &key );
``` 


返回一个指向大于或者等于key值的第一个元素的迭代器。





## max_size

语法: 

 
```
size_type max_size();
``` 


返回当前多元集合能容纳元素的最大限值。





## rbegin

语法: 

 
```
reverse_iterator rbegin();
``` 


返回指向当前多元集合中最后一个元素的反向迭代器。





## rend

语法: 

 
```
reverse_iterator rend();
``` 


返回指向集合中第一个元素的反向迭代器。





## size

语法: 

 
```
size_type size();
``` 


返回当前多元集合中元素的数目。





## swap

语法: 

 
```
void swap( multiset &obj );
``` 


交换当前多元集合和obj多元集合中的元素。





## upper_bound

语法: 

 
```
iterator upper_bound( const key_type &key );
``` 


在当前多元集合中返回一个指向大于Key值的元素的迭代器





## value_comp

语法: 

 
```
value_compare value_comp();
``` 


返回一个用于比较元素间的值的函数对象。
