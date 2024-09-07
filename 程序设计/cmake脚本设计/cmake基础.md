# cmake_minimu_required

`cmake_minimu_required`：为cmake项目配置最小的CMAKE版本
- 语法：`cmake_minimu_required(VERSION <min>[...<policy_max>] [FATAL_ERROR])`
	- `<min>`：最小的版本
	- `[...<policy_max>]`：到最大的版本
	- `[FATAL_ERROR]`

# if...else...endif

`if...else...endif`：条件判断

- 语法：`if(<condition>)[<sentence>]else()[<sentence>]endif()`
	- `<condition>`：判断条件
	- `[<sentence>]`：CMAKE语句
