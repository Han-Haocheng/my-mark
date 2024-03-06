描述
面向切面编程aop是另一个设计思想，spring-aop是spring框架实现这一思想的实现部分。
面向切面
描述
面向切面编程在本质上类似于设计模式中的\<装饰模式\>，在整个程序中，各个模块在实现的过程中，可能出现一些位于模块核心逻辑外的，重复性的非模块逻辑的代码，典型的例子如日志、数据访问等。
概念
aspect - 切面 - 切面类

advice - 增强 - 切面类的方法

target - 目标 - 被增强的类

joinpoint - 链接点 - 被增强的方法

pointcut - 切入点 - 被增强的方法列
引入包
spring-aop

aspectJ
流程 - 以实现日志切面为例
配置切面
xml配置方式
beans引入aop命名空间
xmlns:aop="http://www.springframework.org/schema/aop"
将aop命名空间命名空间映射入beans中
xsi:schemaLocation="

<http://www.springframework.org/schema/aop>

<https://www.springframework.org/schema/aop/spring-aop.xsd>"
开辟aop配置元素
\<aop:config\>\</aop:config\>
在aop配置元素中定义pointcut切点和aspect切面
\<aop:pointcut id="pc" expression="execution(\* aspect.class.package.\*.\*(..))"/\>
注解配置方式

