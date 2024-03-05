---
title: JdbcTemplate
updated: 2024-01-11 09:08:44Z
created: 2024-01-11 09:08:43Z
---

---
title: JdbcTemplate
updated: 2023-11-02T10:17:20.0000000+08:00
created: 2023-10-31T08:43:02.0000000+08:00
---

JdbcTemplate
2023年10月31日
8:43

# 描述
spring提供的jdbc驱动的模板

# 流程
### Xml方式
定义数据源
定义jdbc模板
\<bean id="jdbcTemplate" class="org.springframework.jdbc.core.JdbcTemplate"\>
\<property name="dataSource" ref="data_source"/\>
\</bean\>
### 注释方式

方法
### 数据增加、删除、修改操作
int update(String sql, Object... args);
作用 - 用于对数据源进行增删改操作

参数

sql - 预编译的sql语句

args - sql语句的对应参数

返回 - int - 干涉的行数
### 数据查询操作
List\<T\> query(String sql, RowMapper\<T\> rowMapper);
作用 - 用于对数据源进行查询改操作

参数

sql - 预编译的sql语句

rowMapper - ==排与对象字段的映射关系==

返回 - List\<T\> - 查询到的对象列表
