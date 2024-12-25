cmake_minimum_required(VERSION 3.10)
project(myproject)

# 设置C++标准
set(CMAKE_CXX_STANDARD 11)
# 设置是否必须使用CMAKE_CXX_STANDARD作为C++标准
set(CMAKE_CXX_STANDARD_REQUIRED True)

add_executable(hello src/hello.cpp)