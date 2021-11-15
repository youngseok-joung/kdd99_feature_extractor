# The environment variable PCAPDIR allows to specficy where to find
# libpcap in non standard location.

cmake_minimum_required (VERSION 2.8.12)
project (kdd99extractor CXX C)

# Distributed CMake Find modules
set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${CMAKE_SOURCE_DIR}/cmake/")

#include_directories(BEFORE ${PCAP_INCLUDE_DIR} ${MYSQL_INCLUDE_DIRS})
message(STATUS "CMAKE_SOURCE_DIR=${CMAKE_SOURCE_DIR}")
message(STATUS "ENV{PCAPDIR}=$ENV{PCAPDIR}")
message(STATUS "PCAP_FOUND=${PCAP_FOUND}")
message(STATUS "PCAP_LIBRARIES=${PCAP_LIBRARIES}")
message(STATUS "PCAP_INCLUDE_DIR=${PCAP_INCLUDE_DIR}")
message(STATUS "MYSQL_INCLUDE_DIRS=${MYSQL_INCLUDE_DIRS}")
message(STATUS "MYSQL_LIBRARIES=${MYSQL_LIBRARIES}")

add_subdirectory(src)
