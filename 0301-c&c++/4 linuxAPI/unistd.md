头文件
\#include \<unistd.h\>
函数
int sleep(unsigned int sec);

描述

让线程进入休眠状态

参数

sec - 休眠时间，单位 秒

int access(const char \*pathname, int mode);

描述

检查调用进程是否可以对指定的文件执行某种操作。

参数

pathname - 需要测试的文件路径名。

mode - 需要测试的操作模式，可能值是一个或多个
| 可读     | R_OK |
|----------|------|
| 可写     | W_OK |
| 可执行   | X_OK |
| 文件存在 | F_OK |
返回

成功 - 返回0

失败 - 返回-1，并保存错误值

错误
| EINVAL       | 模式值无效                             |
|--------------|----------------------------------------|
| EACCES       | 文件或路径名中包含的目录不可访问       |
| ELOOP        | 解释路径名过程中存在太多的符号连接     |
| ENAMETOOLONG | 路径名太长                             |
| ENOENT       | 路径名中的目录不存在或是无效的符号连接 |
| ENOTDIR      | 路径名中当作目录的组件并非目录         |
| EROFS        | 文件系统只读                           |
| EFAULT       | 路径名指向可访问的空间外               |
| EIO          | 输入输出错误                           |
| ENOMEM       | 不能获取足够的内核内存                 |
| ETXTBSY      | 对程序写入出错                         |

int unlink(const char \*pathname);

描述

unlink函数删除文件系统中的一个名字，如果这个名字是该文件的最后一个link并且该文件没有被任何进程打开，那么删除该文件。否则等到文件被关闭或最后一个link被删除后删除该文件并释放空间。

参数

pathname - 要删除的文件名

返回

成功 - 返回0

失败 - 返回 -1