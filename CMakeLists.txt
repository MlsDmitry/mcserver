cmake_minimum_required(VERSION 3.1)

project(mcserver)

set(SOURCE_DIR "${PROJECT_SOURCE_DIR}/src")
set(LIB_DIR "${PROJECT_SOURCE_DIR}/lib")

set(CMAKE_CXX_STANDARD_REQUIRED TRUE)
set(CMAKE_CXX_STANDARD 14)
set(CMAKE_BUILD_TYPE DEBUG)

option(RAKNET_ENABLE_STATIC "" FALSE)
add_subdirectory(${LIB_DIR}/RakNet)
file(GLOB SOURCES
	${SOURCE_DIR}/*.cpp
	${SOURCE_DIR}/*.hpp
	${SOURCE_DIR}/*.c
	${SOURCE_DIR}/*.h
	)

add_executable(mcserver ${SOURCES})
target_include_directories(mcserver PRIVATE ${LIB_DIR}/RakNet/Sources)
target_link_libraries(mcserver RakNetDLL)
