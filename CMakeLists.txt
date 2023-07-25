cmake_minimum_required(VERSION 3.25)
project(demo3)

set(CMAKE_CXX_STANDARD 17)
#SET(CMAKE_CXX_COMPILER /usr/bin/g++)
set(FFMPEG_DIR /usr/local/Cellar/ffmpeg/6.0)
set(SDL_DIR /usr/local/Cellar/sdl2/2.28.1)

include_directories(HEAD/ ${FFMPEG_DIR}/include/ ${SDL_DIR}/include/)

link_directories(${FFMPEG_DIR}/lib/ ${SDL_DIR}/lib/)

add_executable(demo3 SRC/main.cpp SRC/log.cpp HEAD/log.h HEAD/avframequeue.h SRC/avframequeue.cpp HEAD/queue.h HEAD/avpacketqueue.h SRC/avpacketqueue.cpp HEAD/thread.h HEAD/demuxthread.h SRC/demuxthread.cpp HEAD/audiooutput.h SRC/audiooutput.cpp SRC/decode.cpp HEAD/videooutput.h SRC/videooutput.cpp HEAD/decode.h)

set(FFMPEG_LIBS
        ${FFMPEG_DIR}/lib/libavcodec.dylib
        ${FFMPEG_DIR}/lib/libavformat.dylib
        ${FFMPEG_DIR}/lib/libswscale.dylib
        ${FFMPEG_DIR}/lib/libavdevice.dylib
        ${FFMPEG_DIR}/lib/libavfilter.dylib
        ${FFMPEG_DIR}/lib/libavutil.dylib
        ${FFMPEG_DIR}/lib/libswresample.dylib)

set(SDL_LIBS
        ${SDL_DIR}/lib/libSDL2-2.0.0.dylib
        ${SDL_DIR}/lib/libSDL2.dylib)


target_link_libraries(demo3 ${FFMPEG_LIBS} ${SDL_LIBS})