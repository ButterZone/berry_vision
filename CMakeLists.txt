cmake_minimum_required(VERSION 2.8)
project( berry_eyes )
# you can see the cmake output on the command line by doing
# set( CMAKE_VERBOSE_MAKEFILE on )

include_directories( ${berry_eyes_SOURCE_DIR}/lib/mavlink )

set( raspicam_DIR "/usr/local/lib/cmake" )

set( SOURCES 
	src/autopilot_interface.cpp
	src/mavlink_control.cpp
	src/serial_port.cpp
	src/camera_interface.cpp )

find_package( raspicam REQUIRED )

find_package( OpenCV REQUIRED )

find_package( Threads )

add_executable( berry_eyes ${SOURCES} )

target_link_libraries( berry_eyes ${CMAKE_THREAD_LIBS_INIT} )
target_link_libraries( berry_eyes ${raspicam_CV_LIBS} )