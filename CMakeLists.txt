cmake_minimum_required(VERSION 2.8)

project(cmake_test_project)

add_executable(cmake_test_executable cmake_test.cpp)

install(TARGETS cmake_test_executable DESTINATION bin)
