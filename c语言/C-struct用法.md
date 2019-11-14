## 声明struct类型
```
struct Student{
    char *name;
};

//声明实例
struct Student stu;   //这里的struct不能省略

//定义别名
typedef struct Student STU;   //struct Student重新定义为STU类型
typedef STU* S;               //
```

## 用typedef声明struct
```
typedef struct
{
    char *name;
}Person;

//声明实例
Person p1;   //这里用了typedef关键字，Person前不用struct
```

## 声明结构时初始化
```
struct Person
{
    char *name;
} p1{
    "p1"
}, p2{
    "p2"
};    //p1,p2为Person的两个实例对象
```


