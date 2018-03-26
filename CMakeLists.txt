cmake_minimum_required(VERSION 2.8)
project(DC)

if (NOT "${CMAKE_CXX_COMPILER_ID}" STREQUAL "MSVC")
	set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -Wextra -pedantic -Werror -Wno-nested-anon-types")
endif()

#SET(CMAKE_RUNTIME_OUTPUT_DIRECTORY bin)

include_directories(${DC_SOURCE_DIR}/src/math)
include_directories(${DC_SOURCE_DIR}/src/vol)
include_directories(${DC_SOURCE_DIR}/src/util)
include_directories(${DC_SOURCE_DIR}/src)

add_executable(dc
	src/main.cpp
	src/math/Math.cpp
	src/math/Solver.cpp
	src/vol/Contouring.cpp
)

add_executable(tests
	src/test.cpp
	src/math/Math.cpp
	src/math/Solver.cpp
	src/vol/Contouring.cpp
)

add_test(core tests)

set_property(TARGET dc tests PROPERTY CXX_STANDARD 11)
