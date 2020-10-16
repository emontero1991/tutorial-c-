cmake_minimum_required(VERSION 3.0.2)
project(test)


find_package(catkin REQUIRED COMPONENTS
  roscpp
  rospy
  std_msgs
  tf
)



catkin_package(
  INCLUDE_DIRS include
  LIBRARIES test

)


include_directories(
# include
  ${catkin_INCLUDE_DIRS}
)


add_executable(helloworld src/helloworld.cpp)

add_dependencies(helloworld ${${PROJECT_NAME}_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})

target_link_libraries(helloworld 
 ${catkin_LIBRARIES}
)
