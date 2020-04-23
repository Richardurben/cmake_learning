cmake_minimum_required(VERSION 2.6) #指定cmake最低版本为2.6

project(RML) # 指定工程名字

include_directories(./TypeIIRML/include)

aux_source_directory(./TypeIIRML/src CPP_LIST0) # 搜索当前目录下的所有CPP文件

aux_source_directory(./Tutorial/RMLPositionSampleApplications CPP_LIST1) 

aux_source_directory(./Tutorial/RMLVelocitySampleApplications CPP_LIST2)

add_executable(typeiirml ${CPP_LIST0} ${CPP_LIST1} ${CPP_LIST2}) # 生成目标文件

