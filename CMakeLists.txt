cmake_minimum_required(VERSION 3.4...3.18)
project(interp)

find_package(Python3 REQUIRED Interpreter Development)

if(NOT Python3_FOUND)
    message(FATAL_ERROR "Python3 libs Not found")
endif()

add_subdirectory(pybind11)

add_executable(interp src/main.cpp)
target_link_libraries(interp PRIVATE pybind11::embed ${PYTHON_LIBRARIES})
target_include_directories(interp PRIVATE ${PYTHON_INCLUDE_DIRS})