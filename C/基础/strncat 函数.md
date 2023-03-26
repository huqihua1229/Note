# strncat 函数

C 库函数 **char *strncat(char *dest, const char *src, size_t n)** 把 **src** 所指向的字符串追加到 **dest** 所指向的字符串的结尾，直到 **n** 字符长度为止。

函数声明：

```c
char *strncat(char *dest, const char *src, size_t n)
```

注意：dest 需要保证后面至少有 n + 1 个未被使用的字节，因为该函数会在字符串结尾加上 '\0'。

例子：

```c
#include <stdio.h>
#include <string.h>

int main(void){
    char a[6] = "aaaaa";
    char b[6] = "bbbbb";
    char c[6] = "ccccc";

    strncat(b, c, 3);

    puts(a);
    puts(b);
    puts(c);

    return 0;
}


```

debug 过程：

* 执行 strcncat(b, c, 3) 之前
  
  <img title="" src="file:///C:/Study/Note/C/picture/屏幕截图%202022-08-19%20092158.png" alt="" data-align="center">

* 执行 strcncat(b, c, 3) 之后
  
  <img src="file:///C:/Study/Note/C/picture/屏幕截图%202022-08-19%20092409.png" title="" alt="" data-align="center">
  
  可以看出 strncat 函数在 a 字符串的后方接上三个 'c' 后又补上了 '\0'。由于 b 剩余的空间无法容纳全部的新字符，而 a 的存储空间与 b 相邻，所以 strncat 便把字符写到了 a 的存储空间中。
  
  说明 strncat 函数和 strcat 函数一样，可能会对相邻已使用的内存空间中的数据造成破坏。
