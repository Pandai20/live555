cmake_minimum_required(VERSION 3.10)
project(live555ProxyServer)

# 设置可执行文件名
set(PROXY_SERVER live555ProxyServer)

# 设置 include 目录
include_directories(
    ../UsageEnvironment/include
    ../groupsock/include
    ../liveMedia/include
    ../BasicUsageEnvironment/include
    /usr/local/include
)

# 设置编译选项
add_compile_definitions(
    SOCKLEN_T=socklen_t
    _LARGEFILE_SOURCE=1
    _FILE_OFFSET_BITS=64
    ALLOW_RTSP_SERVER_PORT_REUSE=1
    BSD=1
)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -O2")
# 设置二进制文件输出目录
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin)
message(STATUS "this is CMAKE_RUNTIME_OUTPUT_DIRECTORY dir " ${CMAKE_RUNTIME_OUTPUT_DIRECTORY})

# 设置源码文件
set(SOURCES
    live555ProxyServer.cpp
)

# 设置依赖库路径
link_directories(
    ../UsageEnvironment
    ../groupsock
    ../liveMedia
    ../BasicUsageEnvironment
    .
)

# 添加可执行文件
add_executable(${PROXY_SERVER} ${SOURCES})


target_link_libraries(${PROXY_SERVER}
    liveMedia
    groupsock
    BasicUsageEnvironment
    UsageEnvironment
    ssl
    crypto
)

# 安装设置
#install(TARGETS ${PROXY_SERVER} DESTINATION bin)
