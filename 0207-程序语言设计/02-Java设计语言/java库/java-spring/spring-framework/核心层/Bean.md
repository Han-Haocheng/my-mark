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

