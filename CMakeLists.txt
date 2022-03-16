cmake_minimum_required(VERSION 2.8 FATAL_ERROR)

# Set project information 
project(test_gstreamer)

add_compile_options(-std=c++11)

find_package(PkgConfig)
pkg_check_modules(GST REQUIRED gstreamer-1.0>=1.2 gstreamer-app-1.0>=1.2)

#file(GLOB_RECURSE Service_SRC "${test_gstreamer_SOURCE_DIR}/src/*.cpp")

include_directories(
	"${test_gstreamer_SOURCE_DIR}/include"
	"${GST_INCLUDE_DIRS}")

link_libraries("${GST_LDFLAGS}" pthread) 

add_executable(hello hello.cpp)

add_executable(basic-tutorial-2 basic-tutorial-2.cpp)

add_executable(playback-tutorial-1 playback-tutorial-1.cpp)



add_executable(playback-tutorial-2 playback-tutorial-2.cpp)
add_executable(playback-tutorial-3 playback-tutorial-3.cpp)