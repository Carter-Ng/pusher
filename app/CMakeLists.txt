cmake_minimum_required(VERSION 3.4.1)

#导入指定目录下的cmakelists.txt
add_subdirectory(src/main/cpp/librtmp)

add_library(
        native-lib

        SHARED

        src/main/cpp/native-lib.cpp)

#导入x264 头文件
include_directories(src/main/cpp/include)
#导入x264 库文件
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -L${CMAKE_SOURCE_DIR}/src/cpp/libs/${ANDROID_ABI}")

target_link_libraries(
        native-lib
        rtmp
        x264
        log)