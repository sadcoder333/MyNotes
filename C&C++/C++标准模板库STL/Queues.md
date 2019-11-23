# Queues


## back 
语法:
``` 
   TYPE &back();
```
 

back()返回一个引用，指向队列的最后一个元素。




## empty 
语法: 
```
  bool empty();
```
 

empty()函数返回真(true)如果队列为空，否则返回假(false)。




## front 
语法:
``` 
   TYPE &front();
```
 

front()返回队列第一个元素的引用。




## pop 
语法:
``` 
  void pop();
```
 

pop()函数删除队列的一个元素。




## push 
语法:
``` 
  void push( const TYPE &val );
```
 

push()函数往队列中加入一个元素。




## size 
语法: 
```
  size_type size();
```
 

size()返回队列中元素的个数。
