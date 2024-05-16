aux_source_directory(./src DIR_examples_SRCS)

include_directories(../lib/Config)
include_directories(../lib/LCD)
include_directories(../lib/QMI8658)
include_directories(../lib/lvgl)
include_directories(./inc)


add_library(examples-LVGL ${DIR_examples_SRCS})
target_link_libraries(examples-LVGL PUBLIC Config-LVGL LCD-LVGL QMI8658-LVGL LVGL hardware_clocks hardware_rtc hardware_adc hardware_i2c hardware_dma hardware_spi hardware_pwm pico_stdlib)
