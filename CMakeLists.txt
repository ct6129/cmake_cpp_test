cmake_minimum_required(VERSION 3.29.0)
project(planning)
set(CMAKE_CXX_STANDARD 17)
# ROJECT_SOURCE_DIR表示CMAKELISTS.txt所在的目录
set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)
# 将当前目录下的所有cpp文件放到SRC_LISTS中
aux_source_directory(. SRC_LISTS)
add_executable(planning_main ${SRC_LISTS})