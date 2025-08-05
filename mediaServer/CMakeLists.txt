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
# 设置编译选项
add_definitions(
    -DSOCKLEN_T=socklen_t
    -D_LARGEFILE_SOURCE=1
    -D_FILE_OFFSET_BITS=64
    -DALLOW_RTSP_SERVER_PORT_REUSE=1
    -DBSD=1
)
add_definitions(-DDEBUG)
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -O0 -Wall")

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

