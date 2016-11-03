cmake_minimum_required(VERSION 2.8.3)
project(aruco)

find_package(catkin REQUIRED COMPONENTS roslint)

find_package(OpenCV REQUIRED)

catkin_package(
  INCLUDE_DIRS include
  LIBRARIES aruco

)

roslint_cpp()


include_directories(
  include
  ${catkin_INCLUDE_DIRS}
  ${OpenCV_INCLUDE_DIRS}
)

add_library(aruco
  src/aruco/arucofidmarkers.cpp
  src/aruco/cvdrawingutils.cpp
  src/aruco/cameraparameters.cpp
  src/aruco/board.cpp
  src/aruco/marker.cpp
  src/aruco/boarddetector.cpp
  src/aruco/markerdetector.cpp
)
target_link_libraries(aruco
  ${catkin_LIBRARIES} ${OpenCV_LIBRARIES})

#############
## Install ##
#############

install(DIRECTORY include/
   DESTINATION ${CATKIN_GLOBAL_INCLUDE_DESTINATION}
   FILES_MATCHING PATTERN "*.h"
)

