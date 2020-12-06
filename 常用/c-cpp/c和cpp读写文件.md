
### c语言读写字符串


#### 使用`fputs`和`fgets`读写文件

1. 引入头文件
```c
#include <stdio.h>
```

2. 写入字符串

```c
void write_file(const char *filename, const char* text)
{
    FILE* fp = fopen(filename, "w");
    if(!fp)
    {
        printf("open file failed: %s\n", filename);
        return;
    }
    fputs(text, fp);
    fclose(fp);
}
```

3. 读取字符串

```c
void read_file(const char* filename)
{
    FILE* fp = fopen(filename, "r");
    if(!fp)
    {
        printf("open file failed %s\n", filename);
        return;
    }
    char buffer[1024];
    fgets(buffer, sizeof(buffer), fp);
    printf("%s\n", buffer);
    fclose(fp);
}
```


#### 使用`fwrite`和`fread`读写文件

1. 引入头文件
```
#include <stdio.h>
```

2. 写入字符串

```c
void write_file(const char *filename, const char* text)
{
    FILE* fp = fopen(filename, "w");
    if(!fp)
    {
        printf("open file failed: %s\n", filename);
        return;
    }

    fwrite(text, sizeof(char), strlen(text), fp);   // #include <string.h>
    fclose(fp);
}
```


3. 读取字符串

```c
void read_file(const char* filename)
{
    FILE* fp = fopen(filename, "r");
    if(!fp){
        printf("open file failed %s\n", filename);
        return;
    }
    char buffer[1024];
    int read_size = fread(buffer, sizeof(char), sizeof(buffer), fp);
    printf("read size : %d\n", read_size);
    printf("read content : %s\n", buffer);
    fclose(fp);
}
```



### cpp读写字符串


1. 引入头文件
```c
#include <iostream>
#include <fstream>
```

2. 写入字符串

```c
void write_file(const char* filename, const char* text) {
    ofstream out(filename, ios::out);
    if(out.bad()) {
        cout << "open file failed " << filename << endl;
        return;
    }
    out << text;
    out.close();
}
```

3. 读取字符串

```c
void read_file(const char* filename)
{
    ifstream in(filename);
    if(out.bad()) {
        cout << "open file failed " << filename << endl;
        return;
    }

    // 逐行读取字符串
    string result;
    while(!in.eof()){
        getline(in, result);
        cout << result << endl;
    }
    in.close();
}
```