# 指定编译所需的CMake最低版本
cmake_minimum_required(VERSION 3.4.1)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=gnu++14 -Wall")

set(bx_dir ./bgfx.cmake/bx)
set(bimg_dir ./bgfx.cmake/bimg)
set(bimg-decode_dir ./bgfx.cmake/bimg/src)
set(dear-imgui_dir ./bgfx.cmake/bgfx/3rdparty/dear-imgui)
set(bgfx_dir ./bgfx.cmake/bgfx)
set(examples-common_dir ./bgfx.cmake/bgfx/examples/common)

set(bgfx_cmake_dir bgfx.cmake)
add_subdirectory(${bgfx_cmake_dir})

set(CMAKE_SHARED_LINKER_FLAGS
        "${CMAKE_SHARED_LINKER_FLAGS} -u ANativeActivity_onCreate")

## 编译成共享库
# add_library(native-activity SHARED main.cpp)
#
## 设置目标库的包含目录
#target_include_directories(native-activity PRIVATE
#        ${ANDROID_NDK}/sources/android/native_app_glue
#        ${bx_dir}/include
#        ${bimg_dir}/include
#        ${bgfx_dir}/include
#        ${bgfx_dir}/3rdparty
#        ${examples-common_dir})
#
## 设置目标库的链接库
#target_link_libraries(native-activity
#        bgfx
#        example-common)
#
## 添加define否则会报错
#target_compile_definitions(
#        native-activity
#        PRIVATE "-D_CRT_SECURE_NO_WARNINGS" #
#        "-D__STDC_FORMAT_MACROS" #
#        "-DENTRY_CONFIG_IMPLEMENT_MAIN=1" #
#        "-DENTRY_CONFIG_USE_NATIVE=1" #
#        "-DBX_PLATFORM_ANDROID=1" #
#)