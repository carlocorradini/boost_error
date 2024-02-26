cmake_minimum_required(VERSION 3.14 FATAL_ERROR)

#
# Project
#
project(
  error
  VERSION 1.0.0
  LANGUAGES CXX
)

#
# Settings
#
set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED TRUE)
set(CMAKE_CXX_EXTENSIONS FALSE)
set(CMAKE_DEBUG_POSTFIX d)
list(APPEND CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR}/cmake)

#
# Options
#
option(BUILD_SHARED_LIBS "Build shared libraries" FALSE)

#
# Includes
#
include(CPM)

#
# Dependencies
#
# https://www.boost.org
add_compile_definitions(BOOST_USE_WINDOWS_H) # FIXME
CPMAddPackage(
  NAME boost
  VERSION 1.84.0
  URL https://github.com/boostorg/boost/releases/download/boost-1.84.0/boost-1.84.0.tar.xz
  URL_HASH SHA256=2e64e5d79a738d0fa6fb546c6e5c2bd28f88d268a2a080546f74e5ff98f29d0e
  EXCLUDE_FROM_ALL TRUE
  SYSTEM TRUE
  OPTIONS "BOOST_ENABLE_CMAKE TRUE" "BOOST_INCLUDE_LIBRARIES log"
)
add_compile_definitions(BOOST_USE_WINDOWS_H) # FIXME

#
# Executable
#
add_executable(${PROJECT_NAME} src/main.cpp)
target_link_libraries(${PROJECT_NAME} PRIVATE Boost::log)
target_compile_definitions(
  ${PROJECT_NAME} PRIVATE # FIXME
                          BOOST_USE_WINDOWS_H
)
