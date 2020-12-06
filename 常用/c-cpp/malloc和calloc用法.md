


**malloc/calloc和realloc都是用于动态分配内存的函数**

#### malloc函数声明
```c
void* __cdecl malloc(
    _In_ _CRT_GUARDOVERFLOW size_t _Size
    );
```

#### calloc函数声明
```c
void* __cdecl calloc(
    _In_ _CRT_GUARDOVERFLOW size_t _Count,
    _In_ _CRT_GUARDOVERFLOW size_t _Size
    );
```

#### realloc函数声明

```c
void* __cdecl realloc(
    _Pre_maybenull_ _Post_invalid_ void*  _Block,
    _In_ _CRT_GUARDOVERFLOW        size_t _Size
    );
```

**除了参数列表有差异之外，calloc分配内存后对内存进行了初始化，malloc和realloc没有**


### 引用头文件
```c
#include <stdlib.h>
```


### 打印工具方法
```c
void print_array(const int* array, const size_t size)
{
    for(size_t i = 0; i < size; i++)
    {
        printf("array[%d] = %d\n", i, array[i]);
    }
}
```

结果如下:
```
array[0] = 4534534
array[1] = 7756534
array[2] = 2312
array[3] = 23123
array[4] = 545465
array[5] = 196453
array[6] = 76876886
array[7] = 78564534
array[8] = 3452323
array[9] = 324
```


### malloc申请分配内存
```c
void test_malloc(){
    size_t size = 10;
    // 申请10个int类型的内存
    int *array = (int *)malloc(sizeof(int) * size);
    if(!array){
        printf("malloc failed\n");
        return;
    }
    print_array(array, size);
    free(array);
}
```

结果如下:
```
array[0] = 0
array[1] = 0
array[2] = 0
array[3] = 0
array[4] = 0
array[5] = 0
array[6] = 0
array[7] = 0
array[8] = 0
array[9] = 0
```


### calloc申请分配内存
```c
void test_calloc(){
    size_t size = 10;
    // 申请10个int类型的内存
    int *array = (int *)calloc(size, sizeof(int));
    if(!array){
        printf("malloc failed\n");
        return;
    }
    print_array(array, size);
    free(array);
}
```

结果如下:
```
array[0] = 0
array[1] = 0
array[2] = 0
array[3] = 0
array[4] = 0
array[5] = 0
array[6] = 0
array[7] = 0
array[8] = 0
array[9] = 0
```


### realloc重新分配内存大小
```c
void test_realloc(){
    size_t size = 10;
    // 申请10个int类型的内存
    int *array = (int *)malloc(sizeof(int) * size);
    if(!array){
        printf("malloc failed\n");
        return;
    }
    size_t new_size = 20;
    // 重新分配内存，容量扩容到20
    array = (int *)realloc(array, new_size);
    print_array(array, new_size);
    free(array);
}
```
结果如下:
```
array[0] = 0
array[1] = 0
array[2] = 0
array[3] = 0
array[4] = 0
array[5] = 0
array[6] = 0
array[7] = 0
array[8] = 0
array[9] = 0
array[10] = 83
array[11] = 0
array[12] = -2144694400
array[13] = 1
array[14] = -552734650
array[15] = 0
array[16] = 544336
array[17] = 6
array[18] = 0
array[19] = 0
```


