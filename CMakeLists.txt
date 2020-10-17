cmake_minimum_required(VERSION 3.0.2)
project(test)


find_package(catkin REQUIRED COMPONENTS
  roscpp
  rospy
  std_msgs
  tf
)

## eigen
find_package(cmake_modules REQUIRED)
list(APPEND CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR}/cmake)
find_package(Eigen REQUIRED)
include_directories(${Eigen_INCLUDE_DIRS})
#  eigen

catkin_package(
  INCLUDE_DIRS include
  LIBRARIES test
  DEPENDS Eigen roscpp rospy tf	    #  eigen
)


include_directories(
# include
  ${catkin_INCLUDE_DIRS}
)


add_executable(talker src/talker.cpp)
add_executable(eigen src/eigen.cpp)




add_dependencies(talker ${${PROJECT_NAME}_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})
add_dependencies(eigen ${${PROJECT_NAME}_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})




target_link_libraries(talker
 ${catkin_LIBRARIES}

)

target_link_libraries(eigen
 ${catkin_LIBRARIES}
 ${Eigen_LIBRARIES}   #  eigen
)



