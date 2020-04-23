# Linux下使用cmake教程
> CMake+Practice.pdf

## 常见使用外部编译
~~~ 
mkdir build
cd build
cmake ..
make(make VERBOSE=1)  or
cmake --build . --config Release
~~~
以上可以在build文件夹里生成makefile等文件，并直接生成可执行文件，其他常用命令还包括：
~~~
make clean
~~~
清除上次的make命令所产生的object文件（后缀为“.o”的文件）及可执行文件。
~~~
make install
~~~
将编译成功的可执行文件安装到系统目录中，一般为/usr/local/bin目录。
~~~
make dist
~~~
产生发布软件包文件（即distribution package）。这个命令将会将可执行文件及相关文件打包成一个tar.gz压缩的文件用来作为发布软件的软件包。
它会在当前目录下生成一个名字类似“PACKAGE-VERSION.tar.gz”的文件。PACKAGE和VERSION，是我们在configure.in中定义的AM_INIT_AUTOMAKE(PACKAGE, VERSION)。
~~~
make distcheck
~~~
生成发布软件包并对其进行测试检查，以确定发布包的正确性。这个操作将自动把压缩包文件解开，然后执行configure命令，并且执行make，来确认编译不出现错误，最后提示你软件包已经准备好，可以发布了。
~~~
cmake -DCMAKE_INSTALL_PREFIX=/tmp/hello/usr
~~~
自定义安装文件夹下，默认安装在/usr/local下

## 进阶(按文件类型生成)
按照文件类型可以建立工程文件框架：
* project
	* CMakeLists.txt
	* README.md
	*  build
		* bin
	* include
		* 头文件.h
	* src
		* 源文件.c
		* CMakeLists.txt
	* lib
		* 库文件.so?

 根目录下的CMakeLists.txt包括：
 ~~~ cmake
 ADD_SUBDIRECTORY(src bin)
 ~~~
 src中的CMakeLists.txt包括：
 
 ~~~ cmake
 INCLUDE_DIRECTORIES(${HELLO_SOURCE_DIR}/include)
 SET(SRC_list
${HELLO_SOURCE_DIR}/src/main.c
${HELLO_SOURCE_DIR}/src/hello.c
)
SET(EXECUTABLE_OUTPUT_PATH ${HELLO_BINARY_DIR}/bin)
ADD_EXECUTABLE(hello ${SRC_list})
...
 ~~~
 
 ## cmake源码包卸载
 找到之前的build文件夹，里面会有一个叫install_manifest.txt的纯文本文件，里面的内容就是你cmake安装的文件，我们只要以这个内容作为变量交给rm指令处理就好：
 ~~~
 cat install_manifest.txt | sudo xargs rm
 ~~~
 ## Notes
**通过外部编译进行工程构建,HELLO_SOURCE_DIR 仍然指代工程路径,即 /(根目录)，而 HELLO_BINARY_DIR 则指代编译路径,即/build.**

## update
RML(Reflexxes Motion Libraries)
