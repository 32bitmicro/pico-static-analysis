aux_source_directory(. DIR_QMI8658_SRCS)

include_directories(../Config)

add_library(QMI8658-LVGL ${DIR_QMI8658_SRCS})
target_link_libraries(QMI8658-LVGL PUBLIC Config-LVGL hardware_adc pico_stdlib)