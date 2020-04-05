#camke最低版本
cmake_minimum_required(VERSION 3.10)

#cmake项目名称
project(cmake_project)

#cmake软件版本
set(CMAKE_SYSTEM_VERSION 1.0)

#cmake指定编译器路径
set(CROSS_TOOLCHAIN_PREFIX "/path/arm-linux-")

#指定编译器
set(CMAKE_C_COMPILE "$(CROSS_TOOLCHAIN_PREFIX)gcc")
set(CMAKE_CXX_COMPILE "$(CROSS_TOOLCHAIN_PREFIX)g++")

#指定默认路径编译器
set(CMAKE_C_COMPILE "gcc")
set(CMAKE_CXX_COMPILE "g++")

#指定编译选项
set(CMAKE_BUILD_TYPE Debug)

#指定编译目录
set(PROJECT_BINARY_DIR $(PROJECT_SOURCE_DIR)/build)

#添加子目录，这样进入源码目录src目录可以继续构建
add_subdirectory($(PROJECT_SOURCE_DIR)/src)


