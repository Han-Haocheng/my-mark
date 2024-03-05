---
title: jUnit框架
updated: 2024-01-11 09:08:52Z
created: 2024-01-11 09:08:51Z
---

---
title: jUnit框架
updated: 2023-11-02T10:49:02.0000000+08:00
created: 2023-11-02T10:13:03.0000000+08:00
---

描述
用于java的单元测试的框架
引入
junit.jar

hamcrest.jar
流程
定义测试类和测试单元
public class JunitTest{

@Test

public void test1(){

//...

}

@Test

public void test2(){

//...

}

}
定义测试单元的增强
public class JunitTest{

@Before

public void testBefore(){

//...

}

@After

public void testAfte(){

//...

}

}

