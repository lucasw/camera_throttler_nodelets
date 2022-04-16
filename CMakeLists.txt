cmake_minimum_required(VERSION 3.0.2)
project(camera_throttler_nodelets)

include($ENV{ROS_ROOT}/core/rosbuild/FindPkgConfig.cmake)

find_package(catkin REQUIRED COMPONENTS nodelet_topic_tools pluginlib sensor_msgs)
catkin_package(
#  INCLUDE_DIRS include
  LIBRARIES camera_throttler_nodelets
  CATKIN_DEPENDS nodelet_topic_tools pluginlib sensor_msgs
#  DEPENDS system_lib
)

include_directories(include ${catkin_INCLUDE_DIRS})

add_library(camera_throttler_nodelets
  src/${PROJECT_NAME}/init.cpp
)

target_link_libraries(camera_throttler_nodelets
  ${catkin_LIBRARIES}
)

install(TARGETS camera_throttler_nodelets camera_throttler_nodelets
#   ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
    LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
#   RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)
