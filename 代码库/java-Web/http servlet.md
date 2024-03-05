---
title: http servlet
updated: 2024-01-11 09:08:14Z
created: 2024-01-11 09:08:12Z
---

---
title: http servlet
updated: 2023-11-29T13:46:44.0000000+08:00
created: 2023-09-17T10:06:05.0000000+08:00
---

类 HttpServlet - abstract class HttpServlet
- 网页执行get操作
void doGet(HttpServletRequest req, HttpServletResponse resp)

输入

req - 网页请求对象

resp - 网页响应对象

输出

void - 无
- 网页执行post操作
void doPost(HttpServletRequest req, HttpServletResponse resp)

输入

req - 网页请求对象

resp - 网页响应对象

输出

void - 无
类 HttpServletRequest
作用范围 - 一次请求中
获取请求转发器
getRequestDispatcher(String url)

输入 - url - 要获取的请求转发的网址

返回

Dispatcher - 转发器

填充参数

void forward(HttpServletRequest req, HttpServletResponse resp)

输入

req - 网页请求对象

resp - 网页响应对象

类 HttpServletResponse
发送重定向
void sendRedirect(String url)

输入 - url - 要发送重定向的页面

返回 - void

