# 标准C数学函数

## abs 
语法: 
 ```
  #include <stdlib.h>
  int abs( int num );
 ```

功能： 函数返回参数num.的绝对值。例如: 
```
    int magic_number = 10;
    cout << "Enter a guess: ";
    cin >> x;
    cout << "Your guess was " << abs( magic_number - x ) << " away from the magic number." << endl;
```

>相关主题:
labs(). 




## acos 

语法: 
```
  #include <math.h>
  double acos( double arg );
``` 

功能：函数返回参数arg的反余弦值。参数arg 应当在-1和1之间。 

>相关主题:
asin(), atan(), atan2(), sin(), cos(), tan(), sinh(), cosh(), and tanh(). 




## asin 

语法: 
```
  #include <math.h>
  double asin( double arg );
``` 

功能：函数返回参数arg的反正弦值。参数arg 应当在-1和1之间。  

>相关主题:
acos(), atan(), atan2(), sin(), cos(), tan(), sinh(), cosh(), and tanh(). 




## atan 

语法: 
```
  #include <math.h>
  double atan( double arg );
``` 

功能：函数返回参数arg的反正切值。 

>相关主题:
asin(), acos(), atan2(), sin(), cos(), tan(), sinh(), cosh(), and tanh(). 




## atan2 

语法: 
```
  #include <math.h>
  double atan2( double y, double x );
``` 

功能：函数计算y/x的反正切值，按照参数的符号计算所在的象限。 

>相关主题:
asin(), acos(), atan(), sin(), cos(), tan(), sinh(), cosh(), and tanh(). 




## ceil 

语法: 
```
  #include <math.h>
  double ceil( double num );
``` 

功能： 函数返回参数不小于num 的最小整数。例如, 
```
    y = 6.04;
    x = ceil( y );
```
x为7.0. 

>相关主题:
floor() and fmod(). 




## cos 

语法: 
```
  #include <math.h>
  double cos( double arg );
``` 

功能： 函数返回参数arg的余弦值，arg以弧度表示给出。 

>相关主题:
asin(), acos(), atan(), sin(), atan2(), tan(), sinh(), cosh(), and tanh(). 




## cosh 

语法: 
```
  #include <math.h>
  double cosh( double arg );
``` 

功能： 函数返回参数arg的双曲余弦值。 

>相关主题:
asin(), acos(), atan(), sin(), atan2(), tan(), sinh(), cos(), and tanh(). 




## div 

语法: 
```
  #include <stdlib.h>
  div_t div( int numerator, int denominator );
``` 

功能： 函数返回参数numerator / denominator的商和余数。结构类型div_t定义在stdlib.h中: 
```
    int quot;     // 商数
    int rem;      // 余数
```
例, 以下代码显示x/y的商和余数: 
```
    div_t temp;
    temp = div( x, y );
    printf( "%d divided by %d yields %d with a remainder of %d\n", x, y, temp.quot, temp.rem );
```
>相关主题:
ldiv(). 




## exp 

语法: 
```
  #include <math.h>
  double exp( double arg );
``` 

功能： 函数返回参数returns e (2.7182818) 的arg次幂。 

>相关主题:
log(). 




## fabs 

语法: 
``` 
  #include <math.h>
  double fabs( double arg );
``` 

功能： 函数返回参数arg的绝对值。 

>相关主题:
abs(). 




## floor 

语法: 
```
  #include <math.h>
  double floor( double arg );
``` 

功能： 函数返回参数不大于arg的最大整数。例如, 
```
    y = 6.04;
    x = floor( y );
```
x的值为6.0. 

>相关主题:
ceil(). 




## fmod 

语法: 
``` 
  #include <math.h>
  double fmod( double x, double y );
``` 

功能： 函数返回参数x/y的余数。

>相关主题:
ceil(), floor(), and fabs(). 




## frexp 

语法: 
```
  #include <math.h>
  double frexp( double num, int *exp );
``` 

功能： 函数将参数num 分成两部分： 0.5 和1之间的尾数（由函数返回）并返回指数exp。转换成如下的科学计数法形式： 
```
    num = mantissa * (2 ^ exp)
```
>相关主题:
ldexp(). 




## labs 

语法: 
``` 
  #include <stdlib.h>
  long labs( long num );
``` 

功能： 函数返回参数num的绝对值。 

>相关主题:
abs(). 




## ldexp 

语法: 
``` 
  #include <math.h>
  double ldexp( double num, int exp );
``` 

功能： 函数返回参数num * (2 ^ exp)。如果发生溢出返回HUGE_VAL。 

>相关主题:
frexp() and modf(). 




## ldiv 

语法: 
``` 
  #include <stdlib.h>
  ldiv_t ldiv( long numerator, long denominator );
```

功能： 函数返回参数numerator / denominator的商和余数。结构类型 ldiv_t 定义在stdlib.h中： 
```
    long quot;    // 商数 
    long rem;     // 余数
```
>相关主题:
div(). 




## log 
语法: 
```
  #include <math.h>
  double log( double num );
``` 

功能： 函数返回参数num的自然对数。如果num为负,产生域错误；如果num 为零，产生范围错误。 

>相关主题:
log10(). 




## log10 

语法: 
``` 
  #include <math.h>
  double log10( double num );
``` 

功能： 函数返回参数num以10为底的对数。如果num为负,产生域错误；如果num 为零，产生范围错误。

>相关主题:
log(). 




## modf 

语法: 
``` 
  #include <math.h>
  double modf( double num, double *i );
``` 

功能： 函数将参数num 分割为整数和小数，返回小数部分并将整数部分赋给i。 

>相关主题:
frexp() and ldexp(). 




## pow 

语法: 
``` 
  #include <math.h>
  double pow( double base, double exp );
``` 

功能： 函数返回以参数base 为底的exp 次幂。如果base为零或负和exp 小于等于零或非整数时,产生域错误。如果溢出，产生范围错误。 

>相关主题:
exp(), log(), and sqrt(). 




## sin 

语法: 

``` 
  #include <math.h>
  double sin( double arg );
```

功能： 函数返回参数arg的正弦值，arg以弧度表示给出。

>相关主题:
asin(), acos(), atan(), cosh(), atan2(), tan(), sinh(), cos(), and tanh(). 




## sinh 
语法: 
```
  #include <math.h>
  double sinh( double arg );
``` 

功能： 函数返回参数arg的双曲正弦值。

>相关主题:
asin(), acos(), atan(), cosh(), atan2(), tan(), sin(), cos(), and tanh(). 




## sqrt 

语法: 

``` 
  #include <math.h>
  double sqrt( double num );
``` 

功能： 函数返回参数num的平方根。如果num为负,产生域错误。

>相关主题:
exp(), log(), and pow(). 




## tan 

语法: 

``` 
  #include <math.h>
  double tan( double arg );
``` 

功能： 函数返回参数arg的正切值，arg以弧度表示给出。 

>相关主题:
asin(), acos(), atan(), cosh(), atan2(), sinh(), sin(), cos(), and tanh(). 


## tanh 

语法: 

``` 
  #include <math.h>
  double tanh( double arg );
``` 

功能： 函数返回参数arg的双曲正切值。 

>相关主题:
asin(), acos(), atan(), cosh(), atan2(), tan(), sin(), cos(), and sinh().
