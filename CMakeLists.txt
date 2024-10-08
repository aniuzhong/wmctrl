cmake_minimum_required(VERSION 3.14...3.22)

set(WMCTRL_VERSION 1.07)

project(wmctrl VERSION ${WMCTRL_VERSION} LANGUAGES C)

find_package(X11 REQUIRED)
find_package(PkgConfig REQUIRED)
pkg_check_modules(GLIB REQUIRED glib-2.0)

set(CMAKE_C_STANDARD 99)
set(CMAKE_C_STANDARD_REQUIRED ON)

add_executable(wmctrl main.c)

target_compile_definitions(wmctrl PRIVATE VERSION="${WMCTRL_VERSION}")

target_include_directories(wmctrl PRIVATE ${GLIB_INCLUDE_DIRS})
target_link_directories(wmctrl PRIVATE ${GLIB_LIBRARY_DIRS})
target_link_libraries(wmctrl PRIVATE X11::X11 X11::Xmu)
target_link_libraries(wmctrl PRIVATE ${GLIB_LIBRARIES})