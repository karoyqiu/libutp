cmake_minimum_required(VERSION 3.8)

project(libutp)
set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 11)

# 第三方库
find_library(librt rt)

add_library(utp STATIC
    utp_internal.cpp utp_utils.cpp utp_hash.cpp utp_callbacks.cpp utp_api.cpp utp_packedsockaddr.cpp
)
target_include_directories(utp INTERFACE "${CMAKE_CURRENT_SOURCE_DIR}")

if(librt)
    target_link_libraries(utp PUBLIC ${librt})
endif()
