cmake_minimum_required(VERSION 3.17)

set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)


set(PICO_BOARD pico CACHE STRING "Board type")

if (PICO_SDK_VERSION_STRING VERSION_LESS "1.4.0")
  message(FATAL_ERROR "Raspberry Pi Pico SDK version 1.4.0 (or later) required. Your version is ${PICO_SDK_VERSION_STRING}")
endif()

project(rp2040-lcd-1.28-lvgl C CXX ASM)

# Initialise the Raspberry Pi Pico SDK
pico_sdk_init()

# LVGL Configuration
set_property(GLOBAL PROPERTY PROP_LV_CONF_PATH ${CMAKE_CURRENT_SOURCE_DIR}/examples/inc/lv_conf.h)

add_subdirectory(./lib/Config)
add_subdirectory(./lib/LCD)
add_subdirectory(./lib/QMI8658)
add_subdirectory(./lib/lvgl)
add_subdirectory(./examples)


include_directories(./examples)
include_directories(./lib/Config)
include_directories(./lib/LCD)
include_directories(./lib/QMI8658)
include_directories(./lib/lvgl)
include_directories(./examples/inc)

# Add executable. Default name is the project name, version 0.1
add_executable(${PROJECT_NAME} main.c)

pico_set_program_name(${PROJECT_NAME}  "${PROJECT_NAME}")
pico_set_program_version(${PROJECT_NAME} "0.1")

pico_enable_stdio_uart(${PROJECT_NAME} 1)
pico_enable_stdio_usb(${PROJECT_NAME}  0)

# Compile options
add_compile_options(-O2)

target_link_libraries(${PROJECT_NAME}  
                      LCD-LVGL
                      QMI8658-LVGL
                      LVGL
                      Config-LVGL
                      examples-LVGL
                      pico_stdlib
                      hardware_spi
                      hardware_i2c
                      hardware_dma
                      )
# Add the standard include files to the build
target_include_directories(${PROJECT_NAME}   PRIVATE
  ${CMAKE_CURRENT_LIST_DIR}
)

pico_add_extra_outputs(${PROJECT_NAME})
