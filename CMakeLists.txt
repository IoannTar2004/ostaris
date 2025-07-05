cmake_minimum_required(VERSION 3.26)
project(ostaris)

set(CMAKE_CXX_STANDARD 23)
set(SOURCE ${CMAKE_CURRENT_SOURCE_DIR}/src)

file(GLOB_RECURSE SOURCE_FILES "${SOURCE}/*.cpp")
file(GLOB_RECURSE HEADER_FILES "${SOURCE}/*.hpp")
add_executable(ostaris ${SOURCE_FILES} ${HEADER_FILES}
        src/sample.c)

include_directories("D:/Program Files (x86)/mingw64/include")
link_directories("D:/Program Files (x86)/mingw64/lib")
file(GLOB_RECURSE TEST_SOURCE_FILES "${SOURCE}/*.cpp")
file(GLOB_RECURSE TEST_HEADER_FILES "${SOURCE}/*.hpp")
list(FILTER TEST_SOURCE_FILES EXCLUDE REGEX ".*/main.cpp$")

add_executable(tests tests/template_test.cpp ${TEST_SOURCE_FILES} ${TEST_HEADER_FILES})
target_link_libraries(tests gtest gtest_main gmock gmock_main)