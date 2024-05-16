cmake_minimum_required(VERSION 3.17)

# initialize the SDK based on PICO_SDK_PATH
# note: this must happen before project()
include(pico_sdk_import.cmake)

project(pico_static_analysis C CXX ASM)
set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)

# initialize the Raspberry Pi Pico SDK
pico_sdk_init()

# example project
add_subdirectory(hello_world)

# rp2040-lcd-1.28
add_subdirectory(rp2040-lcd-1.28)

#rp2040-lcd-1.28-lvgl
add_subdirectory(rp2040-lcd-1.28-lvgl)
