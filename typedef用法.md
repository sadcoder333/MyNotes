
## 定义类型别名
```
typedef int GENDER;   //定义性别类型为int
```

## 定义struct
```
typedef struct
{
    char *name;
    int age;
}Person;        //定义结构类型为Person
```

## 定义指针
```
typedef Person *PERSON;  //定义Person指针类型为PERSON
```

## 定义函数指针类型
```
typedef void(*FUNCTIO)(int, int);  //定义一个函数指针，这个函数返回类型为void,两个参数类型为int
```
