cmake_minimum_required(VERSION 2.8)

project(Layer)
SET(CMAKE_INCLUDE_CURRENT_DIR ON)

FIND_PACKAGE(VTK REQUIRED)
INCLUDE(${USE_VTK_FILE})

if(NOT ${CMAKE_SOURCE_DIR} STREQUAL ${CMAKE_CURRENT_SOURCE_DIR})
  set(Layer_includes ${CMAKE_CURRENT_SOURCE_DIR} PARENT_SCOPE)
endif()

# Allow inheritance of include directories
if(NOT ${CMAKE_SOURCE_DIR} STREQUAL ${CMAKE_CURRENT_SOURCE_DIR})
  set(Layer_includes ${Layer_includes} ${CMAKE_CURRENT_SOURCE_DIR} PARENT_SCOPE)
  set(Layer_libraries ${Layer_libraries} Layer PARENT_SCOPE)
endif()

add_library(Layer Layer.cpp)
TARGET_LINK_LIBRARIES(Layer ${VTK_LIBRARIES})
