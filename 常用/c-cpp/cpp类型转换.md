**C++ 类型转换（C风格的强制转换）：**

在C++基本的数据类型中，可以分为四类：整型，浮点型，字符型，布尔型。其中数值型包括 整型与浮点型；字符型即为char。

- 将浮点型数据赋值给整型变量时，舍弃其小数部分
- 将整型数据赋值给浮点型变量时，数值不变，但是以指数形式存储。
- 将double型数据赋值给float型变量时，注意数值范围溢出。
- 字符型数据可以赋值给整型变量，此时存入的是字符的ASCII码。
- 将一个int，short或long型数据赋值给一个char型变量，只将低8位原封不动的送到char型变量中。 
- 将有符号型数据赋值给长度相同的无符号型变量，连同原来的符号位一起传送。



**C++强制类型转换：**

在C++语言中新增了四个关键字`static_cast`、`const_cast`、`reinterpret_cast`和`dynamic_cast`。这四个关键字都是用于强制类型转换的。

新类型的强制转换可以提供更好的控制强制转换过程，允许控制各种不同种类的强制转换。

C++中风格是`static_cast<type>(content)`。C++风格的强制转换其他的好处是，它们能更清晰的表明它们要干什么。程序员只要扫一眼这样的代码，就能立即知道一个强制转换的目的。 

 

## 1)  static_cast

在C++语言中static_cast用于数据类型的强制转换，强制将一种数据类型转换为另一种数据类型。例如将整型数据转换为浮点型数据。

1. C语言所采用的类型转换方式：

```
int a = 10;
int b = 3;
double result = (double)a / (double)b;
```

 

例1中将整型变量a和b转换为双精度浮点型，然后相除。在C++语言中，我们可以采用static_cast关键字来进行强制类型转换，如下所示。

2. static_cast关键字的使用：

```
int a = 10;
int b = 3;
double result = static_cast<double>(a) / static_cast<double>(b);
```

 

在本例中同样是将整型变量a转换为双精度浮点型。采用static_cast进行强制数据类型转换时，将想要转换成的数据类型放到尖括号中，将待转换的变量或表达式放在元括号中，其格式可以概括为如下形式：  

**用法：static_cast <类型说明符> （变量或表达式）**

**它主要有如下几种用法：**

- 用于类层次结构中基类和派生类之间指针或引用的转换
     进行上行转换（把派生类的指针或引用转换成基类表示）是安全的
     进行下行转换（把基类的指针或引用转换为派生类表示），由于没有动态类型检查，所以是不安全的

- 用于基本数据类型之间的转换，如把int转换成char。这种转换的安全也要开发人员来保证

- 把空指针转换成目标类型的空指针

- 把任何类型的表达式转换为void类型

  >  注意：static_cast不能转换掉expression的const、volitale或者__unaligned属性。

**static_cast:可以实现C++中内置基本数据类型之间的相互转换。**

如果涉及到类的话，static_cast只能在**有相互联系的类型中进行相互转换,**不一定包含虚函数。

 

## 2)  const_cast

在C语言中，const限定符通常被用来限定变量，用于表示该变量的值不能被修改。

**而const_cast则正是用于强制去掉这种不能被修改的常数特性，但需要特别注意的是const_cast不是用于去除变量的常量性，而是去除指向常数对象的指针或引用的常量性，其去除常量性的对象必须为指针或引用。**

**用法：const_cast<type_id> (expression)**
  该运算符用来修改类型的const或volatile属性。除了const 或volatile修饰之外， type_id和expression的类型是一样的。
  常量指针被转化成非常量指针，并且仍然指向原来的对象；
  常量引用被转换成非常量引用，并且仍然指向原来的对象；常量对象被转换成非常量对象。

[例3]一个错误的例子：

```
const int a = 10;
const int * p = &a;
*p = 20;                  //compile error
int b = const_cast<int>(a);  //compile error
```

**在本例中出现了两个编译错误，第一个编译错误是\*p因为具有常量性，其值是不能被修改的；另一处错误是const_cast强制转换对象必须为指针或引用，而例3中为一个变量，这是不允许的！**

 

[例4]const_cast关键字的使用

```cpp
#include<iostream>
using namespace std;
 
int main()
{
    const int a = 10;
    const int * p = &a;
    int *q;
    q = const_cast<int *>(p);
    *q = 20;    //fine
    cout <<a<<" "<<*p<<" "<<*q<<endl;
        cout <<&a<<" "<<p<<" "<<q<<endl;
    return 0;
}
```

在本例中，我们将变量a声明为常量变量，同时声明了一个const指针指向该变量（此时如果声明一个普通指针指向该常量变量的话是不允许的，Visual Studio 2010编译器会报错）。

 

**之后我们定义了一个普通的指针\*q。将p指针通过const_cast去掉其常量性，并赋给q指针。之后我再修改q指针所指地址的值时，这是不会有问题的。**

**最后将结果打印出来，运行结果如下：**
**10 20 20**
**002CFAF4 002CFAF4 002CFAF4**

*查看运行结果，问题来了，指针p和指针q都是指向a变量的，指向地址相同，而且经过调试发现002CFAF4地址内的值确实由10被修改成了20，这是怎么一回事呢？为什么a的值打印出来还是10呢？*

其实这是一件好事，我们要庆幸a变量最终的值没有变成20！变量a一开始就被声明为一个常量变量，不管后面的程序怎么处理，它就是一个常量，就是不会变化的。试想一下如果这个变量a最终变成了20会有什么后果呢？对于这些简短的程序而言，如果最后a变成了20，我们会一眼看出是q指针修改了，但是一旦一个项目工程非常庞大的时候，在程序某个地方出现了一个q这样的指针，它可以修改常量a，这是一件很可怕的事情的，可以说是一个程序的漏洞，毕竟将变量a声明为常量就是不希望修改它，如果后面能修改，这就太恐怖了。

在例4中我们称“*q=20”语句为未定义行为语句，所谓的未定义行为是指在标准的C++规范中并没有明确规定这种语句的具体行为，该语句的具体行为由编译器来自行决定如何处理。对于这种未定义行为的语句我们应该尽量予以避免！

从例4中我们可以看出我们是不想修改变量a的值的，既然如此，定义一个const_cast关键字强制去掉指针的常量性到底有什么用呢？我们接着来看下面的例子。

 

例5：

```cpp
#include<iostream>
using namespace std;
 
const int * Search(const int * a, int n, int val);
 
int main()
{
    int a[10] = {0,1,2,3,4,5,6,7,8,9};
    int val = 5;
    int *p;
    p = const_cast<int *>(Search(a, 10, val));
    if(p == NULL)
        cout<<"Not found the val in array a"<<endl;
    else
        cout<<"hvae found the val in array a and the val = "<<*p<<endl;
    return 0;
}
 
const int * Search(const int * a, int n, int val)
{
    int i;
    for(i=0; i<n; i++)
    {
        if(a[i] == val)
            return &a[i];
    }
    return  NULL;
}
```

 

在例5中我们定义了一个函数，用于在a数组中寻找val值，如果找到了就返回该值的地址，如果没有找到则返回NULL。函数Search返回值是const指针，当我们在a数组中找到了val值的时候，我们会返回val的地址，最关键的是a数组在main函数中并不是const，因此即使我们去掉返回值的常量性有可能会造成a数组被修改，但是这也依然是安全的。

对于引用，我们同样能使用const_cast来强制去掉常量性，如例6所示。

例6：

```cpp
#include<iostream>
using namespace std;
 
const int & Search(const int * a, int n, int val);
 
int main()
{
    int a[10] = {0,1,2,3,4,5,6,7,8,9};
    int val = 5;
    int &p = const_cast<int &>(Search(a, 10, val));
    if(p == NULL)
    cout<<"Not found the val in array a"<<endl;
    else
    cout<<"hvae found the val in array a and the val = "<<p<<endl;
    return 0;
}
 
const int & Search(const int * a, int n, int val)
{
    int i;
    for(i=0; i<n; i++)
    {
        if(a[i] == val)
        return a[i];
    }
    return NULL;
}
```

 **了解了const_cast的使用场景后，可以知道使用const_cast通常是一种无奈之举，同时也建议大家在今后的C++程序设计过程中一定不要利用const_cast去掉指针或引用的常量性并且去修改原始变量的数值，这是一种非常不好的行为。**

 

## 3) reinterpret_cast

在C++语言中，reinterpret_cast主要有三种强制转换用途：***改变指针或引用的类型、将指针或引用转换为一个足够长度的整形、将整型转换为指针或引用类型***。

**用法：reinterpret_cast<type_id> (expression)**
  type-id必须是一个指针、引用、算术类型、函数指针或者成员指针。
  它可以把一个指针转换成一个整数，也可以把一个整数转换成一个指针（先把一个指针转换成一个整数，在把该整数转换成原类型的指针，还可以得到原先的指针值）。
  **在使用reinterpret_cast强制转换过程仅仅只是比特位的拷贝，因此在使用过程中需要特别谨慎！**

例7：

```
int *a = new int;
double *d = reinterpret_cast<double *>(a);
```

在例7中，将整型指针通过reinterpret_cast强制转换成了双精度浮点型指针。

reinterpret_cast可以将指针或引用转换为一个足够长度的整形，此中的足够长度具体长度需要多少则取决于操作系统，如果是32位的操作系统，就需要4个字节及以上的整型，如果是64位的操作系统则需要8个字节及以上的整型。 

 

## 4) dynamic_cast

 **用法：dynamic_cast<type_id> (expression)**

 

**（1）其他三种都是编译时完成的，dynamic_cast是运行时处理的，运行时要进行类型检查。**

**（2）不能用于内置的基本数据类型的强制转换。**

**（3）dynamic_cast转换如果成功的话返回的是指向类的指针或引用，转换失败的话则会返回NULL。**

**（4）使用dynamic_cast进行转换的，基类中一定要有虚函数，否则编译不通过。**

​     **B中需要检测有虚函数的原因：类中存在虚函数，就说明它有想要让基类指针或引用指向派生类对象的情况，此时转换才有意义。**

​    

​    **这是由于运行时类型检查需要运行时类型信息，而这个信息存储在类的虚函数表（关于[虚函数表](http://baike.baidu.com/view/3750123.htm)的概念，详细可见<Inside c++ object model>）中，**

​     **只有定义了虚函数的类才有虚函数表。**

 

 **（5）在类的转换时，在类层次间进行上行转换时，dynamic_cast和[static_cast](http://baike.baidu.com/view/1745207.htm)的效果是一样的。在进行下行转换时，dynamic_cast具有类型检查的功能，比static_cast更安全。**

​    **向上转换，即为子类指针指向父类指针（一般不会出问题）；向下转换，即将父类指针转化子类指针。**

​    ***向下转换的成功与否还与将要转换的类型有关，即要转换的指针指向的对象的实际类型与转换以后的对象类型一定要相同，否则转换失败。\***

​     **在C++中，编译期的类型转换有可能会在运行时出现错误，特别是涉及到类对象的指针或引用操作时，更容易产生错误。Dynamic_cast操作符则可以在运行期对可能产生问题的类型转换进行测试。**

 

**例1：**

```cpp
#include<iostream>
using namespace std;
 
class base
{
public :
    void m(){cout<<"m"<<endl;}
};
 
class derived : public base
{
public:
    void f(){cout<<"f"<<endl;}
};
 
int main()
{
    derived * p;
    p = new base;
    p = static_cast<derived *>(new base);
    p->m();
    p->f();
    return 0;
}
```

本例中定义了两个类：base类和derived类，这两个类构成继承关系。在base类中定义了m函数，derived类中定义了f函数。在前面介绍多态时，我们一直是用基类指针指向派生类或基类对象，而本例则不同了。

本例主函数中定义的是一个派生类指针，当我们将其指向一个基类对象时，这是错误的，会导致编译错误。

但是通过强制类型转换我们可以将派生类指针指向一个基类对象，p = static_cast<derived *>(new base);语句实现的就是这样一个功能，这样的一种强制类型转换时合乎C++语法规定的，但是是非常不明智的，它会带来一定的危险。

在程序中p是一个派生类对象，我们将其强制指向一个基类对象，首先通过p指针调用m函数，因为基类中包含有m函数，这一句没有问题，之后通过p指针调用f函数。一般来讲，因为p指针是一个派生类类型的指针，而派生类中拥有f函数，因此p->f();这一语句不会有问题，但是本例中p指针指向的确实基类的对象，而基类中并没有声明f函数，虽然p->f();这一语句虽然仍没有语法错误，但是它却产生了一个运行时的错误。换言之，p指针是派生类指针，这表明程序设计人员可以通过p指针调用派生类的成员函数f，但是在实际的程序设计过程中却误将p指针指向了一个基类对象，这就导致了一个运行期错误。

**产生这种运行期的错误原因在于static_cast强制类型转换时并不具有保证类型安全的功能，而C++提供的dynamic_cast却能解决这一问题，dynamic_cast可以在程序运行时检测类型转换是否类型安全。**

**当然dynamic_cast使用起来也是有条件的，它要求所转换的操作数必须包含多态类类型（即至少包含一个虚函数的类）。**

 

**例2：**

```cpp
#include<iostream>
using namespace std;
 
class base
{
public :
    void m(){cout<<"m"<<endl;}
};
 
class derived : public base
{
public:
    void f(){cout<<"f"<<endl;}
};
 
int main()
{
    derived * p;
    p = new base;
    p = dynamic_cast<derived *>(new base);
    p->m();
    p->f();
    return 0;
}
```

**在本例中利用dynamic_cast进行强制类型转换，但是因为base类中并不存在虚函数，因此p = dynamic_cast<derived \*>(new base);这一句会编译错误。**

**为了解决本例中的语法错误，我们可以将base类中的函数m声明为虚函数，virtual void m(){cout<<"m"<<endl;}。**

**dynamic_cast还要求<>内部所描述的目标类型必须为指针或引用。**

 

**例3：
**

```cpp
#include<iostream>
#include<cstring>
 
using namespace std;
 
class A
{
   public:
   virtual void f()
   {
       cout<<"hello"<<endl;
       };
};
 
  
 
class B:public A
{
    public:
    void f()
    {
        cout<<"hello2"<<endl;
        };
  
};
 
  
 
class C
{
  void pp()
  {
      return;
  }
};
 
  
 
int fun()
{
    return 1;
}
 
int main()
{
    A* a1=new B;//a1是A类型的指针指向一个B类型的对象
    A* a2=new A;//a2是A类型的指针指向一个A类型的对象
    B* b;
    C* c;
    b=dynamic_cast<B*>(a1);//结果为not null，向下转换成功，a1之前指向的就是B类型的对象，所以可以转换成B类型的指针。
    if(b==NULL)
    {
        cout<<"null"<<endl;
    }
 
    else
    {
        cout<<"not null"<<endl;
    }
 
    b=dynamic_cast<B*>(a2);//结果为null，向下转换失败
    if(b==NULL)
    {
        cout<<"null"<<endl;
    }
 
    else
    {
        cout<<"not null"<<endl;
    }
 
    c=dynamic_cast<C*>(a);//结果为null，向下转换失败
    if(c==NULL)
    {
        cout<<"null"<<endl;
    }
 
    else
    {
        cout<<"not null"<<endl;
    }
 
    delete(a);
    return 0;
}
```