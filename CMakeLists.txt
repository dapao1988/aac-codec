cmake_minimum_required(VERSION 3.2)

#1、添加头文件目录，可以多引用，但是不能缺，因为缺了就编译不过
include_directories(
  "./libAACdec/include"
  "./libAACenc/include"
  "./libFDK/include"
  "./libMpegTPDec/include"
  "./libMpegTPEnc/include"
  "./libPCMutils/include"
  "./libSBRdec/include"
  "./libSBRenc/include"
  "./libSYS/include"
  "./wavreader.h"
  "./win32/getopt.h"
)

#2、添加环境变量，请结合实际项目要求，不是必须的
add_definitions(-D__x86__ -DFDK_INLINE=__inline -DSCALE_INLINE=inline -Dinline=__inline  -D_DEBUG)


#3、源文件
#file(GLOB_RECURSE aac_source_files "${CMAKE_CURRENT_SOURCE_DIR}/*.c")
file(GLOB_RECURSE aac_source_files
  "./libAACdec/*.cpp"
  "./libAACenc/*.cpp"
  "./libFDK/*.cpp"
  "./libMpegTPDec/*.cpp"
  "./libMpegTPEnc/*.cpp"
  "./libPCMutils/*.cpp"
  "./libSBRdec/*.cpp"
  "./libSBRenc/*.cpp"
  "./libSYS/*.cpp"
  "./aac-enc.c"
  "./wavreader.c"
)

#4、设置生成静态库以及名称
#add_library(FDKAACDec STATIC ${aac_source_files})
add_executable (FDKAACDec ${aac_source_files})