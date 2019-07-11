# CC2538ZNP

Here is experimental coordinator firmware for CC2538+CC2592 modules.
To be used with Z2M.

Make use of native USB interface on C2538.

Flash firmware with J-Link. (Choose JTAG or ccJTAG interface).


This is minimal required schematics:

![alt text](https://github.com/antst/CC2538ZNP/raw/master/60423818-46deb400-9bef-11e9-8f71-8024a5a03d4e.png)

Be aware, that if you supply voltage from you USB-UART adapter, this might be not enough, as most of them can not deliver enough to supply CC2538+CC2592.

Be aware that there is no use for USB-UART adapter, as USB is native. Trying to avoid soldering 3 resistors and 2 capacitors by connecting to the USB-UART will not work ). It is native USB. It is not UART. It is not CC2530 )
