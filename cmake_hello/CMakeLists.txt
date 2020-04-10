# 版本最低要求
CMAKE_MINIMUM_REQUIRED(VERSION 2.8)

# 工程名字
PROJECT(HELLO)

# 添加子目录，在build文件夹下生成，格式：ADD_SUBDIRECTORY(source_dir [binary_dir] [EXCLUDE_FROM_ALL])
ADD_SUBDIRECTORY(src bin)

# 打印相关消息消息
MESSAGE(STATUS "THIS IS BINARY DIR" ${HELLO_BINARY_DIR})
MESSAGE(STATUS "THIS IS SOURCE DIR" ${HELLO_SOURCE_DIR})

# 安装README
# INSTALL(FILES README.md DESTINATION share/doc/hello)

# 安装hello.sh
# INSTALL(PROGRAMS hello.sh DESTINATION bin)

# 安装doc中的hello.txt，等价于通过ADD_SUBDIRECTORY加入工程（注意安装的是doc下的文件）
# INSTALL(DIRECTORY doc/ DESTINATION share/doc/hello)




