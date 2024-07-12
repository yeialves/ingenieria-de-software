cmake_minimum_required(VERSION 3.5.0)
project(CMake.2)


#set(CMAKE_CXX_STANDARD 11)


set(CMAKE_BUILD_TYPE Debug)

add_executable(CMake.2 main.cpp)

#cmake -DCMAKE_BUILD_TYPE=Debug ..

#cmake -DCMAKE_CXX_COMPILER=clang++ ..

#set(CMAKE_CXX_FLAG ${CMAKE_CXX_FLAGS} -Werror)
target_compile_features(CMake.2
    PUBLIC 
        cxx_nullptr
    PRIVATE 
        cxx_lambdas
)

target_compile_options(CMake.2 PRIVATE -Werror)
