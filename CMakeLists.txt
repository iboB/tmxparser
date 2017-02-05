cmake_minimum_required(VERSION 2.8)
project(tmxparser)
set(CMAKE_MODULE_PATH ${CMAKE_SOURCE_DIR}/cmake ${CMAKE_MODULE_PATH})

set(CMAKE_CXX_STANDARD 11)

add_definitions(-DUSE_MINIZ)

if(MSVC)
    add_definitions(-D_CRT_SECURE_NO_WARNINGS)
endif()


file(GLOB_RECURSE SOURCES ${PROJECT_SOURCE_DIR}/src/*.cpp)
file(GLOB_RECURSE HEADERS ${PROJECT_SOURCE_DIR}/src/*.h)

set(SOURCES ${SOURCES} ${PROJECT_SOURCE_DIR}/src/miniz.c)

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/../tinyxml2)
set(SOURCES ${SOURCES} ${CMAKE_CURRENT_SOURCE_DIR}/../tinyxml2/tinyxml2.cpp)

add_library(tmxparser STATIC ${SOURCES} ${HEADERS})
