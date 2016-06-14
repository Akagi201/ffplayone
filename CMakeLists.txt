cmake_minimum_required(VERSION 2.8.4)

set(TARGET_NAME ffplayone)

project(${TARGET_NAME})

# This is the directory for our custom CMake modules.
set(CMAKE_MODULE_PATH ${CMAKE_SOURCE_DIR}/cmake)

set(SOURCE_DIR ${CMAKE_SOURCE_DIR}/src)

set(DEPS_DIR ${CMAKE_SOURCE_DIR}/deps)

set(SOURCE_FILES ${SOURCE_DIR}/main.c ${SOURCE_DIR}/ffpllay.c ${SOURCE_DIR}/cmdutils.c)

# Handle config options
include(config)

include_directories("${DEPS_DIR}/include" "/usr/local/include")

link_directories("${DEPS_DIR}/lib" "/usr/local/lib")

add_executable(${TARGET_NAME} ${SOURCE_FILES})

target_link_libraries(${TARGET_NAME} "libavformat.a")

target_link_libraries(${TARGET_NAME} "libavutil.a")

target_link_libraries(${TARGET_NAME} "libavcodec.a")

target_link_libraries(${TARGET_NAME} "libavfilter.a")

target_link_libraries(${TARGET_NAME} "libswscale.a")

target_link_libraries(${TARGET_NAME} "libSDL2.a")
