cmake_minimum_required(VERSION 3.4)

project(APCpp-Glue)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_library(APCpp-Glue SHARED apcpp-glue.cpp apcpp-glue.h Archipelago.h)

target_link_libraries(APCpp-Glue ${CMAKE_CURRENT_SOURCE_DIR}/lib/APCpp.lib)

set(BUILD_SHARED_LIBS OFF CACHE BOOL "" FORCE)
set(ENABLE_TESTING OFF CACHE BOOL "" FORCE)

if (WIN32)
    target_link_libraries(APCpp-Glue ws2_32)
endif(WIN32)