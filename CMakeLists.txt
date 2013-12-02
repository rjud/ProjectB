cmake_minimum_required(VERSION 2.6)

project(ProjectB C)

option(BUILD_WITH_A "Build with A" OFF)

if(BUILD_WITH_A)
  find_package(ProjectA REQUIRED)
endif()

add_executable(ExeB exeb.c)

if(BUILD_WITH_A)
  target_link_libraries(ExeB LibA)
endif()

enable_testing()

add_test(ExeB ExeB)

include(CTest)

install(TARGETS ExeB RUNTIME DESTINATION bin)
