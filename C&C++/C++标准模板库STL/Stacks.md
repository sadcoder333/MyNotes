# Stacks


## 操作
语法:
```
  ==
  <=
  >=
  <
  >
  !=
```
 

所有的这些操作可以被用于堆栈. 相等指堆栈有相同的元素并有着相同的顺序。




## empty
语法:   
```
bool empty();
```
 

如当前堆栈为空，empty() 函数 返回 true 否则返回false.




## pop
语法: 
```
void pop();
```
 

pop() 函数移除堆栈中最顶层元素。

>相关主题:
top(), 


## push
语法:   
```
void push( const TYPE &val );
```
 

 push() 函数将 val 值压栈，使其成为栈顶的第一个元素。如:
```
    stack<int> s;
    for( int i=0; i < 10; i++ )
      s.push(i);
``` 




## size
语法:
```
   size_type size();
```
 

size() 函数返当前堆栈中的元素数目。如:
```
    stack<int> s;
    for( int i=0; i < 10; i++ )
      s.push(i);
    cout << "This stack has a size of " << s.size() << endl;
```    
    




## top
语法:
```
    TYPE &top();
```
 

top() 函数返回对栈顶元素的引用. 举例,如下代码显现和清空一个堆栈。
```
    while( !s.empty() ) {
      cout << s.top() << " ";
      s.pop();
    }
```

>相关主题:
pop(), 