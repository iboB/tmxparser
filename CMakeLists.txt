cmake_minimum_required(VERSION 2.8)
project(tmxparser)

add_definitions(-DUSE_MINIZ)

if(MSVC)
    add_definitions(-D_CRT_SECURE_NO_WARNINGS -D_CRT_NONSTDC_NO_DEPRECATE)
endif()

file(GLOB_RECURSE SOURCES src/*.cpp)
file(GLOB_RECURSE HEADERS src/*.h)

set(SOURCES ${SOURCES} src/miniz.c)

include_directories(../tinyxml2)
set(SOURCES ${SOURCES} ../tinyxml2/tinyxml2.cpp)

add_library(tmxparser STATIC ${SOURCES} ${HEADERS})

target_include_directories(tmxparser INTERFACE src)
