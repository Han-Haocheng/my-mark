yaml-cpp
# 命名空间
namespace YAML
# 头文件
\#include \<yaml/yaml.h\>
# 全局变量
# 全局函数
#### *字符串转yaml节点*
Node Load(string yml_str)
#### *yaml节点转字符串*
string Dump(Node node)
#### *从文件获取yaml节点*
Node LoadFile(string filename);
# 枚举
## Type - yaml类型
Null

# 类
## Node - yaml节点
### 成员函数
#### *以列表的方式放置在最后*
void push_back(std::string node_str);
#### *获取节点的起始/终端迭代器*
iterator begin/end();
#### *判断节点是否是标量/图/列表/已定义/空*
bool IsScalar/Map/Sequence/Defined/Null()
#### *获取标量类型的节点值*
string Scalar()

## iterator - yaml迭代器
### 成员函数
#### *解引用*
iterator_value operator\*()

参数 - 无

返回 - 迭代器所指向的值
#### *自增*
iterator operator++()

参数 - 无

返回 - 下一个节点

