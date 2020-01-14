cmake_minimum_required(VERSION 2.4.6)
include($ENV{ROS_ROOT}/core/rosbuild/rosbuild.cmake)

project(BagFromImages)

rosbuild_init()

FIND_PACKAGE(OpenCV REQUIRED)
FIND_PACKAGE(Boost 1.65.0 COMPONENTS filesystem regex system)

if(Boost_FOUND)
    include_directories(${Boost_INCLUDE_DIRS})
endif()

set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)

rosbuild_add_executable(${PROJECT_NAME}
main.cc
Thirdparty/DLib/FileFunctions.cpp)

target_link_libraries (${PROJECT_NAME} ${OpenCV_LIBS} ${Boost_LIBRARIES} console_bridge)
