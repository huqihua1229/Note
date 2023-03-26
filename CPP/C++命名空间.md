C++ 命名空间

当引用的两个或者多个库中都存在一个名为 fun 的函数时，编译器无法判断具体使用哪个函数。

因此引入了**命名空间**这个概念，专门用于解决上述问题。它可作为附加信息来区分不同库中相同名称的函数、类、变量等。

使用命名空间即定义了上下文，本质上，命名空间就是定义了一个范围。

> 参考链接
> 
> [C++ 命名空间 | 菜鸟教程](https://www.runoob.com/cplusplus/cpp-namespaces.html)

****

# 定义命名空间

命名空间的定义使用关键字 **namespace **

```cpp
namespace namespace_name{
    //代码声明
}
```

为了调用带有命名空间的函数或变量，需要在前面加上命名空间的名称，如下所示：

```cpp
name::code; // code 可以是变量或函数
```

具体实例：

```cpp
#include<iostream>
using namespace std;

//第一个命名空间
namespace first_space{
    void func(){
        cout << "Inside first_space" << endl;
    }
}

//第二个命名空间
namespace second_space{
    void func(){
        cout << "Inside second_space" << endl;
    }
}

int main(){

    //调用第一个命名空间中的函数
    first_space::func();

    //调用第二个命名空间中的函数
    second_space::func();

    return 0;
}
```

当上面的代码被编译和执行后，会产生下列结果

```
Inside first_space 
Inside second_space
```

# using 指令

可以使用 **using namespace** 指令，这样在使用命名空间的时候可以不用在前面加上命名空间名称。这个指令会告诉编译器，后续的代码将使用指定的命名空间中的名称。

具体实例：

```cpp
#include<iostream>
using namespace std;

//第一个命名空间
namespace first_space{
    void func(){
        cout << "Inside first_space" << endl;
    }
}

//第二个命名空间
namespace second_space{
    void func(){
        cout << "Inside second_space" << endl;
    }
}

using namespace first_space;

int main(){

    //调用第一个命名空间中的函数
    func();

    return 0;
}
```

当上面的代码被编译和执行时，它会产生下列结果：

```
Inside first_space
```

using 指令可以用来指定命名空间中的特定项目。例如，如果只打算使用命名空间中的 cout 部分，可以使用如下语句：

```cpp
using std::cout;
```

随后的代码中，在使用 cout 的时候就可以不用哦加上命名空间名称作为前缀名单时 std 命名空间中的其他项目仍需加上命名空间名称作为前缀，如下所示：

```cpp
#include <iostream>
using std::cout;

int main ()
{

   cout << "std::endl is used with std!" << std::endl;

   return 0;
}
```

当上面的代码被编译和执行时，它会产生下列结果：

```
std::endl is used with std!
```

**using** 指令引入的名称遵循正常的范围规则。名称从使用 using 指令开始是可见的，知道该范围结束。此时，在范围外定义的同名实体是隐藏的。

# 不连续的命名空间

命名孔家可以定义在几个不同的部分中，因此命名空间是由几个单独定义的部分组成的。一个命名空间的各个组成部分可以分散在多个文件中。

所以，如果命名空间中的某个组成部分需要请求定义在另一个文件中的名称，则仍然需要声明该名称。下面的命名空间定义可以是定义一个新的命名空间，也可以是为已有的空间增加新元素。

```cpp
namespace namespace_name{
    //代码声明
}
```

# 使用多个 using

可以在同一个源文件中使用多个 using 来使用多个命名空间。

编译器在编译的时候会从所使用的所有变量中找到对应的函数。

但如果两个命名空间中存在同名函数，在写代码的时候没在函数名前指定使用哪个命名空间的函数，编译器会报错。

```cpp
#include<iostream>
using namespace std;
//第一个命名空间
namespace first_space{
    void func_first(){
        cout << "Inside first_space"<< endl;
    }
}

namespace second_space{
   void func_second(){
        cout << "Inside second_space"<< endl;
    } 
}

using namespace first_space;
using namespace second_space;

int main(){

    func_first();
    func_second();

    cout << "success" << endl;

    return 0;
}
```

上述代码编译并执行的结果：

```
Inside first_space
Inside second_space
success
```

# 嵌套的命名空间

命名空间可以嵌套，可以在一个命名空间中定义另一个命名空间，如下所示：

```cpp
namespace namespace_name1{
    //代码声明
    namespace namespace_name2{
        //代码声明
    }
}
```

可以通过使用 :: 运算符来访问嵌套的命名空间中的成员

```cpp
//访问 namespace_name2 中的成员
using namespace namespace_name1::namespace_name2;

//访问 namespace_name1 中的成员
using namespace namespace_name1;
```

具体实例：

```cpp
#include<iostream>
using namespace std;
//第一个命名空间
namespace first_space{
    void func(){
        cout << "Inside first_space"<< endl;
    }

    //第二个命名空间
    namespace second_space{
        void func(){
            cout << "Inside second_space"<< endl;
        }    
    }
}

using namespace first_space::second_space;

int main(){

    func();

    return 0;
}
```

当上面的代码被编译和执行时，会产生下列结果：

```
Inside second_space
```

如果将 using namespace first_space::second_space; 改为 using namespace first_space; 

则输出的是

```
Inside first_space
```

# 关于命名空间内变量和函数及全局变量的使用和作用域

```cpp
#include<iostream>
using namespace std;
namespace A {
    int a = 100;
    namespace B { //嵌套一个命名空间 B
        int a = 20;
    }
}

int a = 200; // 定义一个全局变量

int main(){

    cout <<"A::a ="<< A::a << endl;
    cout <<"A::B::a ="<<A::B::a << endl;
    cout <<"a ="<<a << endl;
    cout <<"::a ="<<::a << endl;

    int a = 30;
    cout <<"a ="<<a << endl;
    cout <<"::a ="<<::a << endl;

    return 0;
}
```

结果：

```
A::a =100
A::B::a =20
a =200   //全局变量 a
::a =200
a =30    //局部变量 
::a =200
```

全局变量 a 表达为 **::a**，用于当有同名的局部变量时来区别两者



# 常见错误

## 错误一：重复声明

```cpp
#include<iostream>
using namespace std;

//第一个命名空间
namespace first_space{
    void func(){
        cout << "Inside first_space" << endl;
    }
}

//补充第一个命名空间
namespace first_space{
    void func(){
        cout << "Inside second_space" << endl;
    }
}

using namespace first_space;

int main(){

    //调用第一个命名空间中的函数
    func();

    return 0;
}
```

编译器输出的信息：

```
.\namespace.cpp:13:10: error: redefinition of 'void first_space::func()'
   13 |     void func(){
      |          ^~~~
.\namespace.cpp:6:10: note: 'void first_space::func()' previously defined here
    6 |     void func(){
      |  
```

## 错误二：在命名空间声明前使用 using

```cpp
#include<iostream>
using namespace std;
using namespace first_space;
//第一个命名空间
namespace first_space{
    void func(){
        cout << "Inside first_space"<< endl;
    }
}


int main(){

    //调用第一个命名空间中的函数
    func();

    return 0;
}
```

编译器输出的信息：

```
    3 | using namespace first_space;
      |                 ^~~~~~~~~~~
.\namespace.cpp: In function 'int main()':
.\namespace.cpp:15:5: error: 'func' was not declared in this scope; did you mean 'first_space::func'?
   15 |     func();
      |     ^~~~
      |     first_space::func
.\namespace.cpp:6:10: note: 'first_space::func' declared here
    6 |     void func(){
      |          ^~~~
PS C:\Study\CProject\CPPStudy\Chapter2> g++ .\namespace.cpp
.\namespace.cpp:3:17: error: 'first_space' is not a namespace-name
    3 | using namespace first_space;
      |     
```

### 错误三：使用暂未被声明的变量

假设命名空间被分为两次进行，在两次声明之间使用了第二次声明中的变量，会报错

## 一个命名冲突的情况

```cpp

```
