cmake_minimum_required(VERSION 3.5)
project(ASCO C)

set(CMAKE_C_STANDARD 11)
set(CMAKE_C_STANDARD_REQUIRED ON)
set(CMAKE_C_EXTENSIONS OFF)

set(ASCO_SRCS
asco.c 
auxfunc_alter.c
auxfunc.c
auxfunc_measurefromlis.c
auxfunc_monte.c
de36.c
errfunc.c
evaluate.c
hooke.c
initialize.c
nmlatest.c
rfmodule.c
)

set(ASCO_HDRS
auxfunc_alter.h
auxfunc.h
auxfunc_measurefromlis.h
auxfunc_monte.h
de.h
errfunc.h
initialize.h
rfmodule.h
version.h)

add_compile_definitions(ASCO)

if(MSVC)
    add_compile_definitions(_CRT_SECURE_NO_WARNINGS)
    if (CMAKE_BUILD_TYPE STREQUAL "Debug")
        set(CMAKE_C_FLAGS "/MP /Zc:preprocessor /Od")
    else()
        set(CMAKE_C_FLAGS "/MP /Zc:preprocessor /Os")
    endif()
else()
    if (CMAKE_BUILD_TYPE STREQUAL "Debug")
        set(CMAKE_C_FLAGS "-Wall -Wextra -fcommon -O0 -g")
    else()
        set(CMAKE_C_FLAGS "-fcommon -Os")
    endif()
endif()


add_executable(asco ${ASCO_SRCS} ${ASCO_HDRS})

if (NOT MSVC)
    target_link_libraries(asco m)
endif()

if(WIN32)
    target_link_libraries(asco ws2_32)
endif()

install(TARGETS asco
    BUNDLE DESTINATION bin COMPONENT Runtime
    RUNTIME DESTINATION bin COMPONENT Runtime
    )
