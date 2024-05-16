aux_source_directory(. DIR_LCD_SRCS)

include_directories(../Config)

add_library(LCD-LVGL ${DIR_LCD_SRCS})
target_link_libraries(LCD-LVGL PUBLIC Config-LVGL hardware_adc hardware_dma hardware_i2c hardware_spi hardware_pwm pico_stdlib)