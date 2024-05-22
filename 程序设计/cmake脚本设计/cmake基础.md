# cmake_minimu_required
语法：`cmake_minimu_required(VERSION <min>[...<policy_max>] [FATAL_ERROR])`

含义：为cmake项目配置最小的CMAKE版本

参数：
- `<min>`：最小的版本
- `[...<policy_max>]`：到最大的版本

# if...else...endif

语法
```CMAKE
if(<condition>)
  # ...
else()
  # ...
endif()
```

含义：条件判断

参数：
  - `<condition>`：判断条件