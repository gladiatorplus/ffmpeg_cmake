# ffmpeg_cmake
cmake and static link  version of ffmpeg.This project just link freetype and ass ,so if you need link other library please reconfigure and remake ffmpeg static library(for example git:https://github.com/gladiatorplus/ffmpeg_study), and then dispalce src/include,src/lib in your include folder,lib folder,finally,link your library by add name of your new link-library to src/CMakeLists.txt 'TARGET_SO_LIBS'. 

warning:first unzip src/lib.zip 


