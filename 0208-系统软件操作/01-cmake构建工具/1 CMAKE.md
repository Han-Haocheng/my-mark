# CMAKE

**cmake**：源码构建管理工具，是描述如何在所有主要硬件和操作系统上配置、构建和安装项目

## 目录
- [1.1 简单的可执行文件或库](1.1%20简单的可执行文件或库.md)


## CMAKE管理项目的工作流

```mermaid
flowchart LR
	A2(Source files)
	A3(Installed files)
	A4(Installed package)
	B1(Build targest)
	B3(Scrips for native build tools)
	subgraph Project 
		A1(CMakeLists.txt)
		A2
	end
	subgraph SourceFiles
		B2(Generated source files)
		A1-->B2
		A2-->B2
	end
	
```

![](../../attachment/png/Pasted%20image%2020241122163009.png)

- **CMake time(configure time)**：是CMake运行时的情况，CMake将处理并配置项目中的`CMakeLists.txt`文件
- **Generation time**：将生成本地构建工具所需的脚本，以执行项目中的后续步骤
- **Build time**：这是在平台和工具原生构建脚本上调用原生构建工具的时候，这些脚本以前是由CMake生成的
	- 将调用编译器，并在特定的构建目录中构建目标(可执行文件和库)

>[!warning]+ 注意：递归的CMake time箭头
> 这看起来令人困惑，但是我们将在本书中多次使用它，用来实现平台无关的构建。

- **CTest time(test time)**：运行项目的测试套件，检查目标是否按预期执行
- **CDash time(report time)**：将测试结果上传到面板，与其他开发人员共享
- **Install time**：将项目的目标、源文件、可执行文件和库从构建目录安装到安装位置
- **CPack time(packaging time)**：将项目打包成源代码或二进制代码以便发布
- **Package install time**：在系统范围内安装新生成的包

