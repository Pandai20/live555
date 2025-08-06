cmake_minimum_required(VERSION 3.10)
project(live555)

# 设置二进制文件输出目录
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin)
message(STATUS "this is CMAKE_RUNTIME_OUTPUT_DIRECTORY dir " ${CMAKE_RUNTIME_OUTPUT_DIRECTORY})

# 静态库/动态库的输出路径（.a, .so, .lib, .dll）
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/lib) #动态库（如 .so, .dll）的输出路径
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/lib) #静态库（如 .a, .lib）的输出路径
message(STATUS "this is CMAKE_LIBRARY_OUTPUT_DIRECTORY / CMAKE_ARCHIVE_OUTPUT_DIRECTORY dir :" ${CMAKE_LIBRARY_OUTPUT_DIRECTORY})

# 设置编译选项
add_definitions(
    -DSOCKLEN_T=socklen_t
    -D_LARGEFILE_SOURCE=1
    -D_FILE_OFFSET_BITS=64
    -DALLOW_RTSP_SERVER_PORT_REUSE=1
    -DBSD=1
    #解决报错‘struct std::atomic_flag’ has no member named ‘test’
    -DNO_STD_LIB
    -DDEBUG
)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -O0 -Wall")

add_subdirectory(liveMedia)

add_subdirectory(BasicUsageEnvironment)

add_subdirectory(UsageEnvironment)

add_subdirectory(groupsock)

#Rtsp代理
#add_subdirectory(proxyServer)

add_subdirectory(mediaServer)