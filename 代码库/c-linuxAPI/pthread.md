# 简介
pthread是linux的多线程库
# 头文件
\#include \<pthread.h\>
# 结构体
## 互斥锁
union pthread_mutex_t{...}
## 旋转锁
typedef volatile int pthread_spinlock_t;
# 函数
## 互斥锁
### 初始化互斥锁
int pthread_mutex_init(

pthread_mutex_t\* mutex,

const pthread_mutexattr_t\*mutexattr

);

描述 - 用于初始化互斥锁

参数

mutex - 互斥锁

mutexattr - 互斥锁的状态

返回 - int

错误
### 销毁互斥锁
int pthread_mutex_destroy (pthread_mutex_t \*mutex);

描述 - 用于销毁互斥锁

参数 - mutex - 互斥锁

返回 - int

错误
### 上锁互斥锁
int pthread_mutex_lock (pthread_mutex_t \*mutex);

描述 - 用于为互斥锁上锁

参数 - mutex - 互斥锁

返回 - int

错误
### 解锁互斥锁
int pthread_mutex_unlock (pthread_mutex_t \*mutex);

描述 - 用于为互斥锁解锁

参数 - mutex - 互斥锁

返回 - int

错误
## 旋转锁
### 初始化旋转锁
int pthread_spin_init (pthread_spinlock_t \*lock, int pshared);

描述 - 用于初始化旋转锁

参数

lock - 旋转锁

pshared - 互斥锁的状态

PTHREAD_PROCESS_PRIVATE - 进程私有的锁

PTHREAD_PROCESS_SHARED - 进程共享的锁

返回 - int

成功 - 0

失败

EAGAIN - 系统没有足够资源

ENOMEM - 内存不足

错误
### 销毁旋转锁
int pthread_spin_destroy (pthread_spinlock_t \*lock);

描述 - 用于销毁旋转锁

参数 - lock - 旋转锁

返回 - int

错误
### 上锁旋转锁
int pthread_spin_lock (pthread_spinlock_t \*lock);

描述 - 用于为旋转锁上锁

参数 - lock - 旋转锁

返回 - int

错误
### 解锁旋转锁
int pthread_spin_unlock (pthread_spinlock_t \*lock);

描述 - 用于为旋转锁解锁

参数 - lock - 旋转锁

返回 - int

错误
