---
title: c++ stl标准库
updated: 2024-01-11 09:06:46Z
created: 2024-01-11 09:06:45Z
---

---
title: c++ stl标准库
updated: 2023-12-25T15:55:00.0000000+08:00
created: 2023-12-06T13:53:57.0000000+08:00
---

map
插入元素 insert
std::pair\<iterator, bool\> insert( const value_type& value );

std::pair\<iterator, bool\> insert(value_type&& value ); // c++17

参数 value 要插入的元素

返回 包含迭代器和bool的对，分别保存插入元素的位置和是否插入成功。

template\<class InputIt\> void insert(InputIt first, InputIt last );

模板 InputIt 输入迭代器

参数

first 起始迭代器

last 末尾迭代器

template\<class P\> std::pair\<iterator, bool\> insert( P&& value ); // c++11

模板 P 插入元素的转移引用

返回 包含迭代器和bool的对，分别保存插入元素的位置和是否插入成功。

iterator insert(iterator pos, const value_type& value ); // c++11

iterator insert(const_iterator pos, value_type&& value );//c++17

iterator insert(const_iterator pos, const value_type& value ); // c++11

template\<class P\>iterator insert(const_iterator pos, P&& value ); // c++11

参数

pos 要插入位置

value 要插入元素

返回 插入元素的位置

void insert(std::initializer_list\<value_type\> ilist );//c++11

参数 ilist 初始化元素列表

insert_return_type insert( node_type&& nh );//c++17

参数 nh 元素节点

返回 元素

iterator insert( const_iterator pos, node_type&& nh );//c++17

参数

pos 要插入位置

nh 元素节点

返回 插入元素的位置
插入元素 emplace
template \<class... Args\>

std::pair\<iterator,bool\> emplace(Args&&...args)

参数

args 元素的构造参数

返回

包含迭代器和bool的对，分别保存插入元素的位置和是否插入成功。
插入元素 emplace_hint
template \<class... Args\>

iterator emplace_hint(const_iterator hint,Args&&...args)

参数

hint 插入新元素的位置

args 元素的构造参数

返回

插入元素的位置；如果因为元素存在而导致插入失败，则返回已存在元素位置。

注：在插入元素时，emplace的效率高于insert的效率，因为insert会构造两次元素，而emplace因为使用了参数转移的技术，只构造了一次元素。
