-lpthread是较为老式的解决方法，pthread新加了对于宏D_REENTRANT的定义，-pthread会被展开为“-D_REENTRANT -lpthread”，它不仅可以链接pthread库，还可以打开系统头文件中的各种多线程支持分支，比如，我们常常使用的错误码标志errno，如果没有定义_REENTRANT，则实现为一个全局变量；若是定义了_REENTRANT，则会实现为每线程独有，从而避免线程竞争错误。

-pthread可移植性较强：在Linux中，pthread是作为一个单独的库存在的（[libpthread.so](https://link.zhihu.com/?target=http%3A//libpthread.so/)），但是在其他Unix变种中却不一定，比如在FreeBSD中是没有单独的pthread库的，因此在FreeBSD中不能使用-lpthread来链接pthread，而使用-pthread则不会存在这个问题，因为FreeBSD的编译器能正确将-pthread展开为该系统下的依赖参数。同样道理，其他不同的变种也会有这样那样的区别，如果使用-lpthread，则可能在移植到其他Unix变种中时会出现问题，为了保持较高的可移植性，我们最好还是使用-pthread（尽管这种做法未被接纳成为C标准，但已基本是事实标准）。

因此建议以后都使用-pthread选项来编译。
