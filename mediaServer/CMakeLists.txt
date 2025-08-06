cmake_minimum_required(VERSION 3.10)
project(mediaServer)

# 设置 include 目录
include_directories(
    ../UsageEnvironment/include
    ../groupsock/include
    ../liveMedia/include
    ../BasicUsageEnvironment/include
    /usr/local/include
)

# 定义源文件
set(SOURCES
    live555MediaServer.cpp
    DynamicRTSPServer.cpp
)

# 设置依赖库路径
link_directories(${CMAKE_ARCHIVE_OUTPUT_DIRECTORY})


add_executable(mediaServer ${SOURCES})

target_link_libraries(mediaServer 
    liveMedia
    groupsock
    BasicUsageEnvironment
    UsageEnvironment
    ssl
    crypto
)

