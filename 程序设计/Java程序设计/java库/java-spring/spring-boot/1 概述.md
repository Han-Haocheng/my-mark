# 依赖管理

Spring Boot的每个版本都提供了一个它所支持的依赖的列表
当你升级Spring Boot本身时，这些依赖也会一同升级

# 启动器

启动器Starters：启动器是一组方便的依赖描述符，可以获得所需的所有Spring和相关技术的一站式商店，而无需搜索样本代码和复制粘贴依赖描述符，快速加载对应依赖。

> 所有启动器的命名都遵循`spring-boot-start-*`，其中`*`是一个特定类别的应用程序。

## 应用启动器

- `spring-boot-starter`：核心启动器，包含自动配置支持、日志和YAML
- `spring-boot-starter-test`：使用JUnit Jupiter、Hamcrest和Mockito等库测试Spring Boot应用程序的启动器。
- `spring-boot-starter-web`：使用 SpringMVC 构建 web (包括 RESTful)应用程序的启动器。使用 Tomcat 作为默认的嵌入式容器

## 生产环境启动器

## 技术实现启动器

# 代码结构

## “default”包

*当一个类不包括 package 的声明时，它被认为是在 “default package” 中。 通常应避免使 “default package”。*

对于使用了 `@ComponentScan`, `@ConfigurationPropertiesScan`, `@EntityScan` 或者 `@SpringBootApplication` 注解的SpringBoot应用程序来说，它可能会造成一个问题：项目中的所有jar里面的所有class都会被读取（扫描）。

## 启动器位置

我们通常建议你将你启动类放在一个根package中，高于其他的类，`@SpringBootApplication`注解一般都是注解在启动类上的。它默认会扫描当前类下的所有子包。

例如，编写一个JPA应用程序，`@Entity`类只有定义在启动类的子包下才能被扫描加载到，`@SpringBootApplication` 默认只会扫描加载你项目工程中的组件。

> 如果你不想使用 `@SpringBootApplication` ，可以用`@EnableAutoConfiguration` 和 `@ComponentScan`注解代替

## 经典项目布局

```path
com  
  +- example  
    +- myapplication  
      +- MyApplication.java  
      +- customer  
        +- Customer.java  
        +- CustomerController.java  
        +- CustomerService.java  
        +- CustomerRepository.java  
      +- order  
        +- Order.java  
        +- OrderController.java  
        +- OrderService.java  
        +- OrderRepository.java
```

## 示例：@SpringBootApplication

```java
import org.springframework.boot.SpringApplication;  
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication  
public class MyApplication {
  public static void main(String[] args) {
    SpringApplication.run(MyApplication.class, args);  
  }
}
```

# Configuration 类

Spring Boot倾向于通过Java代码来进行配置的定义。 虽然也可以使用XML来配置`SpringApplication`，但还是建议通过 `@Configuration` 类来进行配置。

## 导入额外的 Configuration 类

- 不需要把所有的 `@Configuration` 放在一个类中。 `@Import`  注解可以用来导入额外的配置类。
- 可以使用 `@ComponentScan`  来自动扫描加载所有Spring组件，包括 `@Configuration` 类。

## 导入 XML Configuration  

使用基于XML的配置，建议仍然从`@Configuration` 类开始，然后通过`@ImportResource` 注解来加载XML配置文件。

# 开发工具

Spring Boot 提供了一套额外的工具，`spring-boot-devtools`模块可以包含在任何项目中，以在开发期间提供一些有用的特性。

```xml
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-devtools</artifactId>
  <optional>true</optional>
</dependency>
```

## 自动重启

当classpath下的文件发生变化时，Spring Boot会自动重启应用程序。
