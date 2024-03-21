cmake_minimum_required(VERSION 3.1)
project(main)

set(SOURCE_DIR src)
set(INCLUDE_DIR include)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -pthread")

find_package(OpenCV 4 REQUIRED)
include_directories(${OpenCV_INCLUDE_DIRS})

include_directories(${INCLUDE_DIR})
add_library(ThreadCam SHARED ${SOURCE_DIR}/ThreadCam.cpp)

set(${PROJECT_NAME}_SRC ${SOURCE_DIR}/main.cpp)

add_executable( ${PROJECT_NAME} ${${PROJECT_NAME}_SRC} )
target_link_libraries( ${PROJECT_NAME} ${OpenCV_LIBS} ThreadCam)
