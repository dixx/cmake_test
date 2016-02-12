cmake_minimum_required(VERSION 2.8)

project(cmake_test_project)

# for the sake of learning and fiddling around, we do not want to install into the system's paths, but into our own
set(CMAKE_INSTALL_PREFIX ../_install)

add_executable(cmake_test_executable cmake_test.cpp)

install(TARGETS cmake_test_executable DESTINATION bin)
