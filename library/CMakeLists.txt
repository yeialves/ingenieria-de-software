cmake_minimum_required(VERSION 3.5.0)
project(HelloWorldProject)

add_subdirectory(my_library)

add_executable(Hello main.cpp)

target_link_libraries(Hello my_library)



