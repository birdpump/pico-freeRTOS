# Add the executable
add_executable(${ProjectName}
        main.cpp
)

# Include directories
target_include_directories(${ProjectName} PRIVATE
        ${CMAKE_CURRENT_LIST_DIR}
        ${CMAKE_CURRENT_SOURCE_DIR}/../lib
)

# Link libraries
target_link_libraries(${ProjectName}
        pico_stdlib
        hardware_gpio
        hardware_spi
        hardware_timer
        FreeRTOS-Kernel-Heap4
        pico_neopixel
)

# Enable USB output, disable UART output
pico_enable_stdio_usb(${ProjectName} 1)
pico_enable_stdio_uart(${ProjectName} 0)

# Create map/bin/hex/uf2 files
pico_add_extra_outputs(${ProjectName})
