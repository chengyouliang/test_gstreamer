cmake_minimum_required(VERSION 2.8 FATAL_ERROR)

# Set project information 
project(test_gstreamer)

add_compile_options(-std=c++11)

find_package(PkgConfig)
pkg_check_modules(GST REQUIRED gstreamer-1.0>=1.2 gstreamer-app-1.0>=1.2)

file(GLOB_RECURSE Service_SRC "${test_gstreamer_SOURCE_DIR}/src/*.cpp")

# excute bin.
add_executable(test_gstreamer ${Service_SRC})

target_include_directories(test_gstreamer PUBLIC 
	"${test_gstreamer_SOURCE_DIR}/include"
	"${GST_INCLUDE_DIRS}")

target_link_libraries(test_gstreamer "${GST_LDFLAGS}" pthread) 
