cmake_minimum_required(VERSION 3.9)
project(sokoban)

set(CMAKE_CXX_STANDARD 11)
add_definitions(-D_CRT_SECURE_NO_WARNINGS)
add_library(sokoban SHARED library.cpp library.h)
find_package( OpenCV REQUIRED )
include_directories(${OpenCV_INCLUDE_DIRS})
if(WIN32)

else()
find_package (Threads REQUIRED)
endif()
add_executable (sokoban_exe library.cpp play.cpp)
target_link_libraries( sokoban_exe ${OpenCV_LIBS} ${CMAKE_THREAD_LIBS_INIT})