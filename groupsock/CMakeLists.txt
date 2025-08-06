cmake_minimum_required(VERSION 3.10)
project(groupsock)


# 设置头文件搜索路径
include_directories(
    include
    ../UsageEnvironment/include
    ../groupsock/include
    /usr/local/include
)

# 定义源文件
set(SOURCES
    GroupsockHelper.cpp
    GroupEId.cpp
    inet.c 
    Groupsock.cpp
    NetInterface.cpp
    NetAddress.cpp
    IOHandlers.cpp
)

# 构建静态库
add_library(groupsock STATIC ${SOURCES})

# 设置安装路径前缀（可通过 cmake -DCMAKE_INSTALL_PREFIX=/your/path 设置）
#set(INSTALL_INCLUDE_DIR include/BasicUsageEnvironment)
#set(INSTALL_LIB_DIR lib)

# 安装头文件
#install(DIRECTORY include/ DESTINATION ${INSTALL_INCLUDE_DIR}
#        FILES_MATCHING PATTERN "*.hh")

# 安装静态库
#install(TARGETS BasicUsageEnvironment
#       ARCHIVE DESTINATION ${INSTALL_LIB_DIR})
