---
title: 集合 set
updated: 2024-01-11 09:06:54Z
created: 2024-01-11 09:06:52Z
---

---
title: 集合 set
updated: 2023-12-27T09:26:29.0000000+08:00
created: 2023-12-27T09:16:09.0000000+08:00
---

集合 set
2023年12月27日
9:16

set
引入
\#include\<set\>
类
template\<

class Key,

class Hash = std::hash\<Key\>,

class KeyEqual = std::equal_to\<Key\>,

class Allocator = std::allocator\<Key\>

\>class unordered_set

类模板参数

Key 集合的键类型

Hash 键的哈希函数

是包含uint64_t operator()(const Key& k)const;的仿函数

KeyEqual 判断相等函数

Allocator 内存分配器类型

成员函数

成员对象
