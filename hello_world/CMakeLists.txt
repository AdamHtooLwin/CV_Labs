cmake_minimum_required(VERSION 3.20)

project(hello)
set(CMAKE_CXX_STANDARD 14)

add_executable(hello main.cpp)
add_executable(graphics graphics.cpp)

find_package(OpenCV 4.5.2 REQUIRED)
target_include_directories(hello PUBLIC ${OpenCV_INCLUDE_DIRS})
target_link_libraries(hello ${OpenCV_LIBS})
target_include_directories(graphics PUBLIC ${OpenCV_INCLUDE_DIRS})
target_link_libraries(graphics ${OpenCV_LIBS})