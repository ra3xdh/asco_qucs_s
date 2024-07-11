cmake_minimum_required(VERSION 3.5)
project(ASCO C)

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

add_definitions("-DASCO")

if (CMAKE_BUILD_TYPE STREQUAL "Debug")
set(CMAKE_C_FLAGS "-fcommon -Os -g")
else()
set(CMAKE_C_FLAGS "-fcommon -Os")
endif()


add_executable(asco ${ASCO_SRCS} ${ASCO_HDRS})
target_link_libraries(asco m)


install(TARGETS asco
    BUNDLE DESTINATION bin COMPONENT Runtime
    RUNTIME DESTINATION bin COMPONENT Runtime
    )
