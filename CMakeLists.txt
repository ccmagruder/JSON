# Copyright 2022 Caleb Magruder
cmake_minimum_required(VERSION 3.22)

project(JSON)

set(CMAKE_CXX_STANDARD 20)

# Build Google Test Depencency
include(FetchContent)
FetchContent_Declare(
    GoogleTest
    GIT_REPOSITORY https://github.com/google/googletest.git
    GIT_TAG        main
)
set(BUILD_GMOCK OFF)
FetchContent_MakeAvailable(GoogleTest)

add_library(JSON SHARED ${CMAKE_SOURCE_DIR}/src/JSON.cpp
                        ${CMAKE_SOURCE_DIR}/src/Variant.cpp)
target_include_directories(JSON PUBLIC ${CMAKE_SOURCE_DIR}/include)

enable_testing()
add_subdirectory(tests)