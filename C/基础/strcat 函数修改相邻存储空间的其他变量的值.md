# strcat 函数修改相邻存储空间的其他变量的值

```c
#include <stdio.h>
#include <string.h>

int main(void){
    char a[10] = "aaaaaaaaa";
    char b[10] = "bbbbbbbbb";
    char c[5] = "cccc";

    strcat(b, c);

    puts(a);
    puts(b);
    puts(c);

    return 0;
}


/*
    程序执行结果：
    ccc
    bbbbbbbbbcccc
    cccc
/
```

debug 过程

* 执行 strcat(b, c) 之前 a, b, c 三个字符串在内存中的值
  
  <img title="" src="./picture/屏幕截图%202022-08-18%20161331.png" alt="" data-align="center">

* 执行 strcat(b, c) 之后 a, b, c 三个字符串在内存中的值
  
  <img title="" src="./picture/屏幕截图%202022-08-18%20161914.png" alt="" data-align="center">
  
  可以看到 b 存储空间的第 10 个字节被修改为 'c'，同时 a 的存储空间中的前四个字节都被修改为 'c'。
  
  说明在内存中这三个字符串的存储顺序为 c b a，在 b 后面拼接其它字符串时会导致 a 的存储空间中的内容被修改。
  
  
