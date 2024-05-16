cmake_minimum_required(VERSION 3.17)

project(rp2040-lcd-1.28)

# Initialise the Raspberry Pi Pico SDK
pico_sdk_init()


add_subdirectory(./lib/Config)
add_subdirectory(./lib/LCD)
add_subdirectory(./lib/Fonts)
add_subdirectory(./lib/GUI)
add_subdirectory(./lib/QMI8658)
add_subdirectory(./examples)


include_directories(./examples)
include_directories(./lib/Config)
include_directories(./lib/Fonts)
include_directories(./lib/GUI)
include_directories(./lib/LCD)
include_directories(./lib/QMI8658)




add_executable(${PROJECT_NAME} main.c )

# enable usb output, disable uart output
pico_enable_stdio_usb(${PROJECT_NAME} 1)
pico_enable_stdio_uart(${PROJECT_NAME} 1)

# create map/bin/hex/uf2 file etc.
pico_add_extra_outputs(${PROJECT_NAME})

target_link_libraries(${PROJECT_NAME} examples LCD QMI8658 GUI Fonts Config pico_stdlib hardware_spi hardware_i2c )
