cmake_minimum_required(VERSION 3.10)
project(calc C)

add_library(arithmetic SHARED add.c sub.c mul.c dur.c)
target_include_directories(arithmetic PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/inc)

add_executable(prog cal_main.c)
target_include_directories(prog PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/inc)
target_link_libraries(prog PRIVATE arithmetic)
