cmake_minimum_required(VERSION 3.14)

project(fclib LANGUAGES CXX)

set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

set(CMAKE_INCLUDE_CURRENT_DIR ON)


set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)


find_package( Boost 1.56)


include_directories( ${Boost_INCLUDE_DIR} )
include_directories( ${CMAKE_SOURCE_DIR}/../3rdparty/ )
include_directories( ${CMAKE_SOURCE_DIR}/include/ )

set(SOURCES src/test.cpp)

set(HEADERS include/cxxclever/test.h)

set(TESTS test/main.cpp)


add_library(fclib STATIC ${SOURCES} ${HEADERS} )

add_executable(fclib.tests ${HEADERS} ${TESTS})

target_link_libraries(fclib.tests fclib ${Boost_LIBRARIES})


source_group(TREE ${CMAKE_CURRENT_SOURCE_DIR} FILES ${SOURCES} ${HEADERS} ${TESTS} )
