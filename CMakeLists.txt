cmake_minimum_required(VERSION 3.29.0)
project(planning)
set(CMAKE_CXX_STANDARD 17)
# 将动态库和可执行文件都放到bin文件目录下
# linux平台下要使用 CMAKE_LIBRARY_OUTPUT_DIRECTORY
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/bin)
aux_source_directory(${PROJECT_SOURCE_DIR}/src SRC_LISTS)
add_library(common
SHARED
${SRC_LISTS}
)
# 将src里面的cpp能够关联到h文件
target_include_directories(common
PUBLIC
${PROJECT_SOURCE_DIR}/include
)

# ROJECT_SOURCE_DIR表示CMAKELISTS.txt所在的目录
# set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)
# 将当前目录下的所有cpp文件放到SRC_LISTS中
add_executable(planning_main planning_main.cpp)
# 这是让可执行文件可以找到h文件
target_include_directories(planning_main
PUBLIC
${PROJECT_SOURCE_DIR}/include
)
# 将可执行文件链接到动态库，此时需要将动态库和可执行文件放到同一个文件目录下面
target_link_libraries(planning_main
PUBLIC
common
)