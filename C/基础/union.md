union 

union 的两个特征：

* 固定首地址

* 按最大需求开辟一段内存空间



所谓联合体 union，就是在内存中划分了一个足够用的空间，对这个内存空间做什么操作都是可以的。

```c
#include<stdio.h>

union hold {
    int a;
    char c[10];
};

int main(void){
    union hold val;
    char *s = (char *)&val;

    s[0] = 's';
    s[1] = 'i';
    s[2] = 's';
    s[3] = 't';
    s[4] = 'i';
    s[5] = 'n';
    s[6] = 'e';
    s[7] = '\0';
    //在此处打断点并使用 gdb 查看
    printf("%s", val);
}
```

```
//gdb 调试

(gdb) print val
$1 = {a = 1953720691, c = "sistine\000", <incomplete sequence \220>}
(gdb) print &val
$2 = (union hold *) 0x61ff10
(gdb) print s
$3 = 0x61ff10 "sistine"
```


