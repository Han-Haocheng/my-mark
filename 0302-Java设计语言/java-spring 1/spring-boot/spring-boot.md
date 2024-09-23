# 目录


# 描述
springboot：用于快速简单创建独立式生产级的Spring为基础的可运行应用程序

# 注意
- 报错：`Caused by: java.lang.ClassNotFoundException: io.r2dbc.spi.ValidationDepth`
  - 原因：@SpringBootApplication所对应的类位于源代码根目录下，由于约定优于配置原则
  - 解决方式：将@SpringBootApplication所对应的类放置于任何一个包里