sem_open 创建有名信号量

sem_init 创建内存信号量

```c
#include <fcntl.h>
#include <sys/stat.h>
#include <semaphore.h>
sem_t *sem sem_open(const char *name, int oflag);
sem_t *sem sem_open(const char *name, int oflag,
                    mode_t mode,unsinged int value);
//Link with -pthread.
```

```c
#include <semaphore.h>
int sem_init(sem_t *sem, int pshared, unsigned int value);
//Link with -pthread.
```
