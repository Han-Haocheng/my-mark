---
title: Bean
updated: 2024-01-11 09:08:32Z
created: 2024-01-11 09:08:30Z
---

---
title: Bean
updated: 2023-11-01T13:24:26.0000000+08:00
created: 2023-10-31T08:37:04.0000000+08:00
---

Bean
2023年10月31日
8:37

描述
类似于工厂模式的管理类型
流程
定义bean

xml定义方式

\<bean id="beanId" class="class.ref"\>

\<property name"setterName" value="baseTypeValue"\>

\<property name"setterName" ref="otherBeanId"\>

\</bean\>

class注释定义方式

调用bean

通过Context调取bean

引入到其他bean

