cmake_minimum_required(VERSION 3.5)

project(ZED_CAM VERSION 0.1)

set(CMAKE_INCLUDE_CURRENT_DIR ON)

option(LINK_SHARED_ZED "Link with the ZED SDK shared executable" ON)

if (NOT LINK_SHARED_ZED AND MSVC)
    message(FATAL_ERROR "LINK_SHARED_ZED OFF : ZED SDK static libraries not available on Windows")
endif()

if(COMMAND cmake_policy)
	cmake_policy(SET CMP0003 OLD)
	cmake_policy(SET CMP0015 OLD)
endif(COMMAND cmake_policy)

SET(EXECUTABLE_OUTPUT_PATH ".")

find_package(ZED 3 REQUIRED)
find_package(OpenCV 4 REQUIRED)

IF(NOT WIN32)
    add_definitions(-Wno-format-extra-args)
    SET(SPECIAL_OS_LIBS "pthread" "X11")
ENDIF()
include_directories(${ZED_INCLUDE_DIRS})
include_directories(${OpenCV_INCLUDE_DIRS})

link_directories(${ZED_LIBRARY_DIR})
link_directories(${OpenCV_LIBRARY_DIRS})

set(PROJECT_SOURCES
    main.cpp
)

add_executable(record ${PROJECT_SOURCES})

if (LINK_SHARED_ZED)
    SET(ZED_LIBS ${ZED_LIBRARIES})
else()
    SET(ZED_LIBS ${ZED_STATIC_LIBRARIES})
endif()

target_link_libraries(record ${ZED_LIBS} ${OpenCV_LIBRARIES})
