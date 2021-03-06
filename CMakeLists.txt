cmake_minimum_required(VERSION 3.1)

project(digger)
set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${PROJECT_SOURCE_DIR}/cmake")

set(SOURCE_FILES
main.cpp
digger.cpp
drawing.cpp
sprite.cpp
scores.cpp
record.cpp
sdl_timer.cpp
sdl_snd.cpp
sound.cpp
newsnd.cpp
ini.cpp
input.cpp
monster.cpp
bags.cpp
alpha.cpp
vgagrafx.cpp
title_gz.cpp
icon.cpp
sdl_kbd.cpp
sdl_vid.cpp
)

set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY build)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY build)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY bin)

find_package(SDL2 REQUIRED)
find_package(SDL2_image REQUIRED)
find_package(zlib REQUIRED)

add_definitions("-DSDL_MAIN_HANDLED")

include_directories(${SDL2_INCLUDE_DIR} ${SDL2_IMAGE_INCLUDE_DIRS} ${ZLIB_INCLUDE_DIR})
link_libraries(${LIBS} ${SDL2_LIBRARY} ${SDL2_IMAGE_LIBRARIES} ${ZLIB_LIBRARY})

if(APPLE)
link_libraries(objc)
elseif(WIN32)
link_libraries(winmm imm32 version ole32 gdi32 oleaut32)
endif()

if(MINGW OR MSYS)
link_libraries(-mwindows)
endif()

add_executable(digger ${SOURCE_FILES})
