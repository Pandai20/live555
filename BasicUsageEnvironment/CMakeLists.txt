cmake_minimum_required(VERSION 3.10)
project(BasicUsageEnvironment)

# 设置头文件搜索路径
include_directories(
    include
    ../UsageEnvironment/include
    ../groupsock/include
    /usr/local/include
)

# 设置编译选项
add_definitions(
    -DSOCKLEN_T=socklen_t
    -D_LARGEFILE_SOURCE=1
    -D_FILE_OFFSET_BITS=64
    -DALLOW_RTSP_SERVER_PORT_REUSE=1
    -DBSD=1
    #解决报错‘struct std::atomic_flag’ has no member named ‘test’
    -DNO_STD_LIB
)


set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -O2 -Wall")


# 定义源文件
set(SOURCES
    BasicUsageEnvironment0.cpp
    BasicUsageEnvironment.cpp
    BasicTaskScheduler0.cpp
    BasicTaskScheduler.cpp
    DelayQueue.cpp
    BasicHashTable.cpp
)

# 构建静态库
add_library(BasicUsageEnvironment STATIC ${SOURCES})

# 设置安装路径前缀（可通过 cmake -DCMAKE_INSTALL_PREFIX=/your/path 设置）
#set(INSTALL_INCLUDE_DIR include/BasicUsageEnvironment)
#set(INSTALL_LIB_DIR lib)

# 安装头文件
#install(DIRECTORY include/ DESTINATION ${INSTALL_INCLUDE_DIR}
#        FILES_MATCHING PATTERN "*.hh")

# 安装静态库
#install(TARGETS BasicUsageEnvironment
#       ARCHIVE DESTINATION ${INSTALL_LIB_DIR})
