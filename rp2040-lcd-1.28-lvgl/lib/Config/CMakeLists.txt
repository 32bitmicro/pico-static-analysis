aux_source_directory(. DIR_Config_SRCS)

add_library(Config-LVGL ${DIR_Config_SRCS})
target_link_libraries(Config-LVGL PUBLIC pico_stdlib hardware_spi hardware_i2c hardware_pwm hardware_adc hardware_dma)
