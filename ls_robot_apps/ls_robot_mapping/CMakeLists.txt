cmake_minimum_required(VERSION 2.8.3)
project(ls_robot_mapping)

add_compile_options(-std=c++11)

find_package(catkin
    REQUIRED COMPONENTS
            roscpp
            rospy
            geometry_msgs
            sensor_msgs
            nav_msgs
            tf
)

catkin_package(
    INCLUDE_DIRS
            include
    CATKIN_DEPENDS
            roscpp
            rospy
            geometry_msgs
            sensor_msgs
            nav_msgs
            tf
)

include_directories(include
    ${catkin_INCLUDE_DIRS}
)

add_executable(ls_robot_mapper src/mapper.cpp src/wangbx_robot_mapper.cpp)
add_dependencies(ls_robot_mapper ${${PROJECT_NAME}_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})
target_link_libraries(ls_robot_mapper ${catkin_LIBRARIES})
