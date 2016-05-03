cmake_minimum_required(VERSION 2.8.3)
project(robbie_2dslam)

find_package(catkin REQUIRED)

catkin_package(
  CATKIN_DEPENDS
    gmapping
)

install(DIRECTORY launch/
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/launch
)
