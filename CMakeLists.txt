cmake_minimum_required(VERSION 3.17)

# initialize the SDK based on PICO_SDK_PATH
# note: this must happen before project()
include(pico_sdk_import.cmake)

project(pico_static_analysis)

# initialize the Raspberry Pi Pico SDK
pico_sdk_init()

# example project
add_subdirectory(hello_world)