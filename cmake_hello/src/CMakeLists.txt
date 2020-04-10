# 头文件路径,自定义位置，..为上一级目录
INCLUDE_DIRECTORIES(${HELLO_SOURCE_DIR}/include)

# 源码路径,默认为工程根目录下
SET(SRC_list
${HELLO_SOURCE_DIR}/src/main.c
${HELLO_SOURCE_DIR}/src/hello.c
)
# 可执行二进制的输出路径为 build/bin 和库的输出路径为 build/lib.
# SET(LIBRARY_OUTPUT_PATH ${HELLO_BINARY_DIR}/lib)
SET(EXECUTABLE_OUTPUT_PATH ${HELLO_BINARY_DIR}/bin)

# 将指定的源文件生成链接文件，然后添加到工程中去
# ADD_LIBRARY(${HELLO_NAME} SHARED 源文件可多个)

# 生成可执行文件
ADD_EXECUTABLE(hello ${SRC_list})

# 将生成的可执行文件与库文件相连
# TARGET_LINK_LIBRARIES(hello 库的路径可多个...)
