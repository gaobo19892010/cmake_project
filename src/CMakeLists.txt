#查找当前所有源文件，并将文件名称保存在DIR_LIB_SRCS目录
#aux_source_directory(. DIR_LIB_SRCS)

#制定头文件目录，PROJECT_SOURCE_DIR为工程的根目录
include_directories($(PROJECT_SOURCE_DIR)/include)

#指定可执行文件的输出目录，输出到bin下面
set(EXCUTABLE_OUTPUT_PATH $(PROJECT_SOURCE_DIR)/bin)

# Lib_demo.cpp生成动态库
add_library(shared_demo SHARED Lib_demo.cpp)
#设置库输出名为shared =》libshared.so
set_target_properties(shared_demo PROPERTIES OUTPUT_NAME "shared")

# Lib_demo.cpp生成静态库
add_library(shared_demo STATIC Lib_demo.cpp)
#设置库输出名为shared =》libshared.a
set_target_properties(shared_demo PROPERTIES OUTPUT_NAME "static")

#指定库文件输出路径
set(LIBRARY_OUTPUT_PATH $(PROJECT_SOURCE_DIR)/lib)

#再指定目录下查找库，并保存在LIBPATHS变量中
find_library(LIBPATHS shared $(PROJECT_SOURCE_DIR)/lib)

#指定生成目标
add_executable(main main.cpp)

#链接共享库
target_link_libraries(main $(LIBPATHS))

