cmake_minimum_required(VERSION 3.15)
project(test_package LANGUAGES C)

find_package(mozjpeg REQUIRED CONFIG)

add_executable(${PROJECT_NAME} test_package.c)
if(TARGET mozjpeg::jpeg)
    target_link_libraries(${PROJECT_NAME} PRIVATE mozjpeg::jpeg)
else()
    target_link_libraries(${PROJECT_NAME} PRIVATE mozjpeg::jpeg-static)
endif()
