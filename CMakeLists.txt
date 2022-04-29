cmake_minimum_required(VERSION 3.2)
project(demo
    VERSION 0.0.1
)

find_package(GTest REQUIRED)
find_package(Threads REQUIRED)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -pthread -Wall -D_GLIBCXX_USE_NANOSLEEP -DLINUX -DHAS_VSOMEIP_BINDING")
set(CMAKE_BUILD_TYPE Debug)
include(GoogleTest)

add_executable(gtest_demo
    src/gtest_demo.cpp
)
target_link_libraries(gtest_demo
    ${GTEST_BOTH_LIBRARIES}
    ${CMAKE_THREAD_LIBS_INIT}
)

gtest_discover_tests(gtest_demo) 
#include("GNUInstallDirs")
