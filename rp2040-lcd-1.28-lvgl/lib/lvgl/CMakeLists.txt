file(GLOB_RECURSE SOURCES ${CMAKE_CURRENT_LIST_DIR}/src/*.c)
# file(GLOB_RECURSE EXAMPLE_SOURCES ${CMAKE_CURRENT_LIST_DIR}/examples/*.c)

add_library(LVGL ${SOURCES})
# add_library(LVGL_EXAMPLE STATIC ${EXAMPLE_SOURCES})
# LVGL configuration
get_property(LV_CONF_PATH GLOBAL PROPERTY PROP_LV_CONF_PATH)
target_compile_definitions(LVGL PRIVATE -DLV_CONF_PATH=${LV_CONF_PATH})

include_directories(${CMAKE_SOURCE_DIR}/examples/inc)
include_directories(${CMAKE_CURRENT_LIST_DIR})

