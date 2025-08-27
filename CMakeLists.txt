cmake_minimum_required(VERSION 3.10)
project(calc C)


add_library(arithmetic SHARED
  add.c
  sub.c
  mul.c
  dur.c
)
target_include_directories(arithmetic PUBLIC
  ${CMAKE_CURRENT_SOURCE_DIR}/inc
)


add_executable(calc
  cal_main.c
)
target_include_directories(calc PRIVATE
  ${CMAKE_CURRENT_SOURCE_DIR}/inc
)


target_link_libraries(calc PRIVATE arithmetic)


set_target_properties(calc PROPERTIES
  INSTALL_RPATH "\$ORIGIN/../lib"
)


install(TARGETS calc arithmetic
  RUNTIME DESTINATION bin
  LIBRARY DESTINATION lib
  ARCHIVE DESTINATION lib
)
