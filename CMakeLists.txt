cmake_minimum_required(VERSION 3.13)

set(PROJECT_NAME "boost")
project(${PROJECT_NAME})
add_library(${PROJECT_NAME} STATIC IMPORTED GLOBAL)


if(MINGW32)
    set_property(TARGET ${PROJECT_NAME} PROPERTY
    IMPORTED_LOCATION ${CMAKE_CURRENT_BINARY_DIR}/lib/mingw-gcc/*)
    target_include_directories(${PROJECT_NAME} INTERFACE ${CMAKE_CURRENT_BINARY_DIR}/include/mingw-gcc)
else()
    set_property(TARGET ${PROJECT_NAME} PROPERTY
    IMPORTED_LOCATION ${CMAKE_CURRENT_BINARY_DIR}/lib/gcc/*)
    target_include_directories(${PROJECT_NAME} INTERFACE ${CMAKE_CURRENT_BINARY_DIR}/include/gcc)
endif()


