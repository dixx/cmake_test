cmake_minimum_required(VERSION 2.8)
project(cmake_test_project)

if(NOT CMAKE_CONFIGURATION_TYPES AND NOT CMAKE_BUILD_TYPE)
   set(CMAKE_BUILD_TYPE Debug)
endif()

message("OS: ${CMAKE_SYSTEM_NAME}")
message("Build type: ${CMAKE_BUILD_TYPE}")

##########################
# variable declarations
####

# for the sake of learning and fiddling around, we do not want to install into the system's paths, but into our own
set(CMAKE_INSTALL_PREFIX ../_install)

# compiler flags
set(CMAKE_CXX_FLAGS_RELEASE "${CMAKE_CXX_FLAGS_RELEASE} -O3")
set(CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS_DEBUG} -O0 -g3")
set(CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS_DEBUG} -D_DEBUG_MODE=1") # switch for additional debug stuff deep in the code
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -DNULL=0") # sadly this is required by LUA
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -c")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -fmessage-length=0")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -m32")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -Wextra -Werror -Wno-aggregate-return -Wlong-long -Winline -Wunreachable-code -Wunused -Wunused-function -Wunused-label -Wunused-parameter -Wunused-value -Wunused-variable -Wuninitialized -Wreturn-type -Wparentheses -Wpointer-arith -Wmissing-braces -Wfloat-equal -Wconversion -Wcast-align")

# directories
set(APP_SOURCE_DIR sources/app)
set(TESTS_SOURCE_DIR sources/test)
set(RESOURCES_DIR resources)
# file lists
file(GLOB sources ${APP_SOURCE_DIR}/*.cpp ${APP_SOURCE_DIR}/*.h)
file(GLOB sources_for_tests ${TESTS_SOURCE_DIR}/*.cpp ${TESTS_SOURCE_DIR}/*.h)
set(sources_for_tests ${sources_for_tests} ${sources})
list(REMOVE_ITEM sources_for_tests ${CMAKE_SOURCE_DIR}/${APP_SOURCE_DIR}/main.cpp)

# TODO use find_library and pass the result from that to target_link_libraries
# NOTE target_link_libraries does not need add_dependencies afterwards

include("${CMAKE_SOURCE_DIR}/irrlicht.cmake")
include("${CMAKE_SOURCE_DIR}/irrklang.cmake")


##########################
# build rules
####

# the executable and the files necessary for it's creation
add_executable(cmake_test_executable ${sources})
# the unit tests
add_executable(unit_tests ${sources_for_tests})

include_directories(${IRRLICHT_INCLUDE_DIR} ${IRRKLANG_INCLUDE_DIR})
target_link_libraries(cmake_test_executable ${IRRLICHT_LIBRARY})
target_link_libraries(unit_tests ${IRRLICHT_LIBRARY})


##########################
# installation rules
####

# on installation, put everything where it belongs
install(TARGETS cmake_test_executable DESTINATION .)
install(TARGETS unit_tests DESTINATION ../_test)
install(DIRECTORY ${RESOURCES_DIR} DESTINATION .)
