cmake_minimum_required(VERSION 3.0)
project(craft)
#set(CMAKE_VERBOSE_MAKEFILE ON)
#add_compile_options(-std=c++11)
add_definitions(-std=c99 -O3)
#glew static lib
add_compile_options(-DGLEW_STATIC)

#FILE(GLOB SOURCE_FILES src/*.c)

aux_source_directory(src SOURCE)
aux_source_directory(deps/lodepng SOURCE)
aux_source_directory(deps/noise SOURCE)
aux_source_directory(deps/sqlite SOURCE)
aux_source_directory(deps/tinycthread SOURCE)

include_directories(src)
include_directories(deps/lodepng)
include_directories(deps/noise)
include_directories(deps/sqlite)
include_directories(deps/tinycthread)

include_directories(deps/GLEW/include)
include_directories(deps/GLFW/include)
include_directories(deps/curl/include)

link_directories (${PROJECT_SOURCE_DIR}/deps/GLEW/lib/Release/Win32)
link_directories (${PROJECT_SOURCE_DIR}/deps/GLFW/lib-vc2015)
link_directories (${PROJECT_SOURCE_DIR}/deps/curl/lib)

add_executable(${PROJECT_NAME} ${SOURCE})
target_link_libraries(${PROJECT_NAME} PRIVATE Opengl32 ws2_32 glfw3 glew32s curl)
