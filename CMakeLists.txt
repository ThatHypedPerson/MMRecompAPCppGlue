cmake_minimum_required(VERSION 3.4)

project(APCpp-Glue)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

SET(CMAKE_SKIP_BUILD_RPATH  FALSE)
SET(CMAKE_BUILD_WITH_INSTALL_RPATH TRUE)
SET(CMAKE_INSTALL_RPATH "$\{ORIGIN\}")

add_library(APCpp-Glue SHARED apcpp-glue.cpp apcpp-glue.h Archipelago.h)

set(BUILD_SHARED_LIBS OFF CACHE BOOL "" FORCE)
set(ENABLE_TESTING OFF CACHE BOOL "" FORCE)

if (WIN32)
    target_link_libraries(APCpp-Glue ${CMAKE_CURRENT_SOURCE_DIR}/lib/APCpp.lib)
    target_link_libraries(APCpp-Glue ws2_32)
else()
    target_link_libraries(APCpp-Glue ${CMAKE_CURRENT_SOURCE_DIR}/lib/libAPCpp.so)
endif(WIN32)