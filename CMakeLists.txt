cmake_minimum_required(VERSION 3.10)
project(live555)

# 设置二进制文件输出目录
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin)
message(STATUS "this is CMAKE_RUNTIME_OUTPUT_DIRECTORY dir " ${CMAKE_RUNTIME_OUTPUT_DIRECTORY})

# 静态库/动态库的输出路径（.a, .so, .lib, .dll）
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/lib) #动态库（如 .so, .dll）的输出路径
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/lib) #静态库（如 .a, .lib）的输出路径
message(STATUS "this is CMAKE_LIBRARY_OUTPUT_DIRECTORY / CMAKE_ARCHIVE_OUTPUT_DIRECTORY dir :" ${CMAKE_LIBRARY_OUTPUT_DIRECTORY})

add_subdirectory(liveMedia)

add_subdirectory(BasicUsageEnvironment)

add_subdirectory(UsageEnvironment)

add_subdirectory(groupsock)

#Rtsp代理
#add_subdirectory(proxyServer)

add_subdirectory(mediaServer)