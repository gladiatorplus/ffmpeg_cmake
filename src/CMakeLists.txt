CMAKE_MINIMUM_REQUIRED(VERSION 3.5)
PROJECT(test)

aux_source_directory(${PROJECT_SOURCE_DIR} DIR_SRCS)
set (TEST_FFMPEG
    ${DIR_SRCS}
    )

include_directories(include) #include
include_directories(${CMAKE_INCLUDE_CURRENT_DIR})
include_directories(${CMAKE_CURRENT_BINARY_DIR})

link_directories(lib) #lib

add_executable(${PROJECT_NAME} ${TEST_FFMPEG} ${PROJECT_INCLUDE}) #编译执行文件

target_include_directories(${PROJECT_NAME} PUBLIC ${TEST_FFMPEG}) #添加ffmpeg文件夹

set(TARGET_LIBS
    ${PROJECT_SOURCE_DIR}/lib/libavfilter.a
    ${PROJECT_SOURCE_DIR}/lib/libavformat.a
    ${PROJECT_SOURCE_DIR}/lib/libavdevice.a
    ${PROJECT_SOURCE_DIR}/lib/libavcodec.a
    ${PROJECT_SOURCE_DIR}/lib/libswscale.a
    ${PROJECT_SOURCE_DIR}/lib/libavutil.a
    ${PROJECT_SOURCE_DIR}/lib/libswresample.a
    )
# -lsndio -lXext -lasound -lSDL2 -lmp3lame
#-lxcb-shm -lxcb -lxcb-render -lxcb-shape -lxcb-xfixes
# -lx264 -lXv  -lpostproc
#-lc -lraw1394 -lavc1394 -lrom1394 -liec61883 -ljack -ldrm -lopenal
#-lcdio_paranoia -lcdio_cdda -ldc1394 -lGL -lcaca -lpulse -lbs2b
#-llilv-0 -ldl -lrubberband -lmysofa -lflite_cmu_us_awb -lflite_cmu_us_kal
#-lflite_cmu_us_kal16 -lflite_cmu_us_rms -lflite_cmu_us_slt -lflite
#-lfribidi -lvidstab -lzmq -lfontconfig -lxml2 -lgme -lopenmpt -lchromaprint
#-lbluray -lgnutls -lssh-gcrypt -lvpx -lwebpmux -lwebp -lrsvg-2 -lgobject-2.0
#-lglib-2.0 -lcairo -lzvbi -lsnappy -laom -lcodec2 -lgsm

set(TARGET_SO_LIBS
    -lz -lpthread -lm  -lX11 -lvdpau -lfreetype -lass -lcrystalhd -lva -lva-drm -llzma -lbz2 -lva-x11)

target_link_libraries(  #添加链接库
    ${PROJECT_NAME}
    ${TARGET_LIBS}
    ${TARGET_SO_LIBS}
    )

set(EXECUTABLE_OUTPUT_PATH #设置可执行程序路径
    ${CMAKE_CURRENT_SOURCE_DIR}
)
