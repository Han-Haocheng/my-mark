# 描述
用于保存一个数据库链接，存放于对应链接池中
# 流程
定义DataSource的bean
### Xml方式 - 以c3p0举例
\<bean id="dataSource" class="com.mchange.v2.c3p0.ComboPooledDataSource"\>

\<property name="driverClass" value="\${driver}"/\>

\<property name="jdbcUrl" value="\${url}"/\>

\<property name="user" value="\${user}"/\>

\<property name="password" value="\${password}"/\>

\<property name="initialPoolSize" value="\${c3p0.initialPoolSize}"/\>

\<property name="maxPoolSize" value="\${c3p0.maxPoolSize}"/\>

\<property name="minPoolSize" value="\${c3p0.minPoolSize}"/\>

\</bean\>
使用DataSource的bean
在代码中获取DataSource

将DataSource引入到其他bean（比如JdbcTemplate）
