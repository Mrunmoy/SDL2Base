cmake_minimum_required(VERSION 3.10)

set(CMAKE_CXX_STANDARD 17)

project(SDL2Test)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${CMAKE_SOURCE_DIR}/cmake/")

set(SDL2_DIR "${CMAKE_CURRENT_LIST_DIR}/SDL2-2.0.20")
set(SDL2_INCLUDE_DIR "${CMAKE_CURRENT_LIST_DIR}/SDL2-2.0.20/include")
set(SDL2_LIB_DIR "${CMAKE_CURRENT_LIST_DIR}/SDL2-2.0.20/lib/x64")
set(SDL2_IMAGE_INCLUDE_DIR "${CMAKE_CURRENT_LIST_DIR}/SDL2-2.0.20/include")

find_package(SDL2 REQUIRED)
find_package(SDL2_image REQUIRED)

message(STATUS, "${SDL2_INCLUDE_DIRS}")
message(STATUS, "${SDL2_IMAGE_INCLUDE_DIRS}")


include_directories(${SDL2_INCLUDE_DIRS} "${CMAKE_CURRENT_LIST_DIR}/include")
include_directories(${SDL2_IMAGE_INCLUDE_DIRS})

set(SOURCE src/main.cpp)

add_executable(SDL2Test WIN32 ${SOURCE})
target_link_libraries(SDL2Test ${SDL2_LIBRARIES} ${SDL2_IMAGE_LIBRARIES})

file(COPY ${SDL2_DIR}/lib/x64/SDL2.dll
    DESTINATION ${CMAKE_CURRENT_BINARY_DIR}/Debug)
