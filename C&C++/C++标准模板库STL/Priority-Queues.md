# Priority Queues




## empty 
语法:
``` 
  bool empty();
```
 

empty()函数返回真(true)如果优先队列为空，否则返回假(false)。




## pop 
语法:
``` 
  void pop();
```
 

pop()函数删除优先队列中的第一个元素。




## push 
语法: 
```
  void push( const TYPE &val );
```
 

push()函数添加一个元素到优先队列中，值为val。




## size 
语法: 
```
  size_type size();
```
 

size()函数返回优先队列中存储的元素个数。




## top 
语法: 
```
   TYPE &top();
```
 

top()返回一个引用，指向优先队列中有最高优先级的元素。注意只有pop()函数删除一个元素。
