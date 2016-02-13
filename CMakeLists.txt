cmake_minimum_required(VERSION 2.8)
project(cmake_test_project)

# for the sake of learning and fiddling around, we do not want to install into the system's paths, but into our own
set(CMAKE_INSTALL_PREFIX ../_install)
# compiler flags
set(CMAKE_CXX_FLAGS "-g -Wall")

# the executable and the files necessary for it's creation
add_executable(cmake_test_executable cmake_test.cpp)
# on installation, put the executable into it's own subfolder
install(TARGETS cmake_test_executable DESTINATION bin)
