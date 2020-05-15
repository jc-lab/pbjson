cmake_minimum_required(VERSION 3.8)
project(pbjson)

set(CMAKE_CXX_STANDARD 11)

if(NOT RapidJSON_INCLUDE_DIRS)
    find_package(RapidJSON REQUIRED)
endif()

set(SRC_FILES
        ${CMAKE_CURRENT_SOURCE_DIR}/src/bin2ascii.h
        ${CMAKE_CURRENT_SOURCE_DIR}/src/pbjson.hpp
        ${CMAKE_CURRENT_SOURCE_DIR}/src/pbjson.cpp
        )

add_library(pbjson STATIC ${SRC_FILES})
target_include_directories(pbjson
        PUBLIC
        ${RapidJSON_INCLUDE_DIRS}
        ${PROTOBUF_IMPORT_DIRS}
        )

target_include_directories(pbjson
        INTERFACE
        ${CMAKE_CURRENT_SOURCE_DIR}/src
        )

