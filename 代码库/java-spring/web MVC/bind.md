---
title: bind
updated: 2024-01-11 09:08:50Z
created: 2024-01-11 09:08:49Z
---

---
title: bind
updated: 2023-12-06T14:30:45.0000000+08:00
created: 2023-11-29T14:17:20.0000000+08:00
---

bind
请求映射
@RequestMapping(

String name() default "";

String\[\] value

String\[\] path

RequestMethod\[\] method

String\[\] params

String\[\] headers

String\[\] consumes

String\[\] produces);

注释类型 类/方法

参数

value/path - 映射的网址路径

method - 请求方式

produces - 请求结果类型
GET请求映射
@GetMapping
请求数据绑定
@RequestParam(String name);

注释类型 - 参数

参数 - name 绑定的请求名字

