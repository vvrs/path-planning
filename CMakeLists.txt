#Project name
project(PathPlanning)

#Version
cmake_minimum_required (VERSION 3.5)
add_definitions(-std=c++11 -g  -Wall)

#Enable warnings
set(CXX_FLAGS "-Wall")
set(CMAKE_CXX_FLAGS "${CXX_FLAGS}")

#src files
# file(GLOB sources "./*.cpp")
file(GLOB sources "./src/*.cpp")
ADD_LIBRARY(LibsModule
    ${sources}
)

target_link_libraries(LibsModule -lyaml-cpp)
target_link_libraries(LibsModule libyaml-cpp.a)
target_link_libraries(LibsModule -L./yaml)

#header files
include_directories(include)

#Destination file
add_executable(pathplanner Main.cpp ${sources})
target_link_libraries(pathplanner LibsModule)