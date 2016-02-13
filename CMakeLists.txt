cmake_minimum_required(VERSION 2.8)
project(cmake_test_project)


##########################
# variable declarations
####

# for the sake of learning and fiddling around, we do not want to install into the system's paths, but into our own
set(CMAKE_INSTALL_PREFIX ../_install)

# compiler flags
set(CMAKE_CXX_FLAGS "-g -Wall")
# directories
set(APP_SOURCE_DIR sources/app)
set(TESTS_SOURCE_DIR sources/test)
set(RESOURCES_DIR resources)
# file lists
file(GLOB sources ${APP_SOURCE_DIR}/*.cpp ${APP_SOURCE_DIR}/*.h)
file(GLOB sources_for_tests ${TESTS_SOURCE_DIR}/*.cpp ${TESTS_SOURCE_DIR}/*.h)
set(sources_for_tests ${sources_for_tests} ${sources})
list(REMOVE_ITEM sources_for_tests ${CMAKE_SOURCE_DIR}/${APP_SOURCE_DIR}/main.cpp)


##########################
# build rules
####

# the executable and the files necessary for it's creation
add_executable(cmake_test_executable ${sources})
# the unit tests
add_executable(unit_tests ${sources_for_tests})


##########################
# installation rules
####

# on installation, put everything where it belongs
install(TARGETS cmake_test_executable DESTINATION .)
install(TARGETS unit_tests DESTINATION ../_test)
install(DIRECTORY ${RESOURCES_DIR} DESTINATION .)
