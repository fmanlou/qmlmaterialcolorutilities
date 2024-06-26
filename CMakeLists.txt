cmake_minimum_required(VERSION 3.22)

project(qmlhtc LANGUAGES C CXX)

set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

include(materialcolorutilities/MaterialColorUtilities.cmake)

if(NOT QT_VERSION_MAJOR)
  set(QT_VERSION_MAJOR 6)
endif(NOT QT_VERSION_MAJOR)

find_package(
  Qt${QT_VERSION_MAJOR}
  COMPONENTS Core Quick
  REQUIRED)

set(Qt_LIBS Qt${QT_VERSION_MAJOR}::Core Qt${QT_VERSION_MAJOR}::Quick)

add_subdirectory(src)

option(QMLMATERIALCOLORUTILITIES_BUILD_DEMO
       "Build QmlMaterialColorUtilities's demo" ON)
option(QMLMATERIALCOLORUTILITIES_BUILD_WITH_SANITIZE
       "Build QmlMaterialColorUtilities With Sanitize Check" ON)

if(QMLMATERIALCOLORUTILITIES_BUILD_DEMO)
  add_subdirectory(demo)
endif(QMLMATERIALCOLORUTILITIES_BUILD_DEMO)
