cmake_minimum_required(VERSION 2.8.3)
project(omnirob_robin_object_detection)

## Find catkin macros and libraries
## if COMPONENTS list like find_package(catkin REQUIRED COMPONENTS xyz)
## is used, also find other catkin packages
find_package(catkin REQUIRED COMPONENTS
  geometry_msgs
  roscpp
  std_msgs
  message_generation
  diagnostic_msgs
  pcl_ros
  omnirob_robin_msgs
)

# Generate used messages and services
# generate_messages(DEPENDENCIES std_msgs diagnostic_msgs omnirob_robin_msgs)

catkin_package(
#  INCLUDE_DIRS include
#  LIBRARIES omnirob_robin_driver
#  CATKIN_DEPENDS geometry_msgs/Twist roscpp std_msgs
#  DEPENDS system_lib
)

include_directories(
  ${catkin_INCLUDE_DIRS}
  include
)

add_executable(omnirob_robin_object_detection src/object_detection.cpp src/robin_odlib.cpp src/robin_odlib_ros.cpp src/robin_object.cpp)
add_dependencies(omnirob_robin_object_detection omnirob_robin_msgs_gencpp)
target_link_libraries(omnirob_robin_object_detection ${catkin_LIBRARIES})
