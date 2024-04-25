cmake_minimum_required(VERSION 3.14)
project(video-app C CXX)
set(CMAKE_CXX_STANDARD 14)

add_subdirectory(lib/glfw)

if(WIN32)
    list(APPEND EXTRA_LIBS
        glu32 opengl32
    )
    set(CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} /mwindows")
else()
    list(APPEND EXTRA_LIBS
        GL GLU X11
    )
endif()

add_executable(video-app src/main.cpp)
target_link_libraries(video-app glfw ${EXTRA_LIBS})