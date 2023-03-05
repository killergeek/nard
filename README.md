# NARD
Nard a dual sim/sam card interface for the flipper zero

# INFO
Its made to make working with smart card interface type ISO7816 easyer on the flipper.\
It fits on top of the flipper with a easy breakout on the back so the IO is still available and you can plug in other modules.\
Just make  sure those are not using PC0 and PC1. because those are used on the NARD.\
PC0 and PC1 are used as a serial port to cummunicatie with the SEC1210.

When you buy the SEC1210 make sure its the UART version not the USB!\
And they come pre programmed with firmware from Microchip.\
And use the CCID commans to interface: https://www.usb.org/sites/default/files/DWG_Smart-Card_CCID_Rev110.pdf

For information about how to communicate with the SEC1210: https://microchip.my.site.com/s/article/SEC1210-URT--Minimal-UART-Testing-on-Windows

Example of a serial command send to the SEC1210:

See below details for this CCID command (hex):\
Hex Bytes: 03 06 62 00 00 00 00 01 01 00 00 00 67\
*Byte 0 : SYNC (0x03)\
 *Byte 1 : CTRL (0x06)\
 *Byte 2 onwards:10 bytes of CCID header + data length: CCID command\
 *Last Byte: LRC (XOR of all the previous bytes)

so: SYNC, CTRL, <CCID commmand>, LRC

The SEC1210 information: https://www.microchip.com/en-us/product/SEC1210

sim card slot used. \
slot1: 115J-BCO0 \
slot2: 115J-ACO0 \
you can find the sim sockets by https://www.tme.eu/

slot1 has the 2 extra pads C4 and C8.
