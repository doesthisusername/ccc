cmake_minimum_required(VERSION 2.8.11)
project(ccc)

if(NOT CMAKE_BUILD_TYPE)
  set(CMAKE_BUILD_TYPE Release)
endif()

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)
if(MSVC)
	# TODO
else()
	set(CMAKE_CXX_FLAGS_DEBUG "-g")
	set(CMAKE_CXX_FLAGS_RELEASE "-O3")
endif()

add_library(ccc STATIC
	ccc/util.cpp
	ccc/elf.cpp
	ccc/mdebug.cpp
	ccc/stabs.cpp
	ccc/ast.cpp
	ccc/print.cpp
)

add_executable(stdump stdump.cpp)
target_link_libraries(stdump ccc)
