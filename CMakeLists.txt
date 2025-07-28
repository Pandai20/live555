cmake_minimum_required(VERSION 3.10)
project(live555)

# 设置二进制文件输出目录
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin)
message(STATUS "this is CMAKE_RUNTIME_OUTPUT_DIRECTORY dir " ${CMAKE_RUNTIME_OUTPUT_DIRECTORY})

add_subdirectory(liveMedia)

add_subdirectory(BasicUsageEnvironment)

add_subdirectory(UsageEnvironment)

add_subdirectory(groupsock)

add_subdirectory(proxyServer)