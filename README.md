# STM32F4_DFU_Demo
STM32F4 USB DFU Demo using STM32F407 Discovery Board

This is a demo of jumping to the system memory bootloader from your application
The demo flashing led project was built in STM32CubeMX and then changes made to main.c and startup_stm32f407xx.s files. 
The blue user button on the board is set up as an interrupt. Whenever the button is pressed a bootloader_is_requested
flag is set to 1. This flag is checked in the main loop. If the flag is set, a special boot value is stored in RAM and
a software reset is performed. On reset, the RAM is checked to see if the special boot value is present. If not, it continues
to the main application. If the flag is set then it jumps to the system memory bootloader.

Notes:
All stm32f4 variants have the same bootloader address, so this code should work for other STM32F4s
The USB DFU will not work if there is no external crystal.
The DFU bootloader requires *.dfu files. These can be converted from the application hex files using ST's DFU File Manger and downloaded
with ST's DfuSe Demo application.
