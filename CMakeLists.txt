cmake_minimum_required(VERSION 3.10)
project(usb2812 C)

set(CMAKE_C_STANDARD 90)

SET(MCU "atmega32u2")
SET(F_CPU "16000000")
SET(CMAKE_SYSTEM_NAME Generic)


# For some reason, these paths have to be absolute, otherwise
# CLion won't be able to find headers etc.
SET(CMAKE_C_COMPILER /usr/bin/avr-gcc)
SET(CMAKE_CXX_COMPILER /usr/bin/avr-g++)

SET(CMAKE_C_FLAGS "-mmcu=${MCU} -DF_CPU=${F_CPU} -Os")
SET(CMAKE_C_LINK_FLAGS "-mmcu=${MCU}")

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/bin")

SET(CMAKE_FIND_ROOT_PATH_MODE_PROGRAM NEVER)
SET(CMAKE_FIND_ROOT_PATH_MODE_LIBRARY ONLY)
SET(CMAKE_FIND_ROOT_PATH_MODE_INCLUDE ONLY)


add_executable(usb2812 test.c usb.c SPIPrinting.c avrUsbUtils.c)

#Besipiele wie es wetier gehen kann
#ADD_EXECUTABLE(${PROJECT_NAME} ${SOURCE_FILES})
#ADD_CUSTOM_COMMAND(TARGET ${PROJECT_NAME} POST_BUILD COMMAND avr-objcopy -O ihex -R.eeprom ${CMAKE_RUNTIME_OUTPUT_DIRECTORY}/${PROJECT_NAME} ${CMAKE_RUNTIME_OUTPUT_DIRECTORY}/${PROJECT_NAME}.hex)
#ADD_CUSTOM_COMMAND(TARGET ${PROJECT_NAME} POST_BUILD COMMAND avr-objcopy -O ihex -j .eeprom --set-section-flags=.eeprom="alloc,load"  --change-section-lma .eeprom=0 ${CMAKE_RUNTIME_OUTPUT_DIRECTORY}/${PROJECT_NAME} ${CMAKE_RUNTIME_OUTPUT_DIRECTORY}/${PROJECT_NAME}.eep)
#ADD_CUSTOM_COMMAND(TARGET ${PROJECT_NAME} POST_BUILD COMMAND avr-size ${CMAKE_RUNTIME_OUTPUT_DIRECTORY}/${PROJECT_NAME} --mcu=${DEVICE} --format=avr)
