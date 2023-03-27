cmake_minimum_required(VERSION 3.13)

# initialize the SDK based on PICO_SDK_PATH
# note: this must happen before project()
include(pico_sdk_import.cmake)

project(ags02ma)

# initialize the Raspberry Pi Pico SDK
pico_sdk_init()

add_executable(ags02ma ags02ma.c)

# pull in common dependencies and additional i2c hardware support
target_link_libraries(ags02ma pico_stdlib hardware_i2c)

# enable usb output, disable uart output
pico_enable_stdio_usb(ags02ma 1)
pico_enable_stdio_uart(ags02ma 0)

# create map/bin/hex file etc.
pico_add_extra_outputs(ags02ma)
