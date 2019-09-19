# CC2538ZNP

Here is experimental coordinator firmware for CC2538+CC2592 modules.
To be used with zigbee2mqtt, ioBroker and the rest.

Make use of native USB interface on C2538.

For programming, you will need J-link and I bellow included pinout for that for typical 20-pin interface.
You can use native segger application ("J-Flash" or "J-Flash lite") for flashing or you can flash from IAR.
Alternatively, if you don't have j-link, you can flash via any Raspberry Pi by using OpenOCD.
Once you do it - write little instruction how and I will add it here :)

This is minimal required schematics to use CC2538 (pinout for module I use):

![alt text](https://github.com/antst/CC2538ZNP/raw/master/60423818-46deb400-9bef-11e9-8f71-8024a5a03d4e.png)

Be aware, that if you supply voltage from you USB-UART adapter, this might be not enough, as most of them can not deliver enough to supply CC2538+CC2592.

Power regulator circuit (surrounded by dashed line) can be replaced by cheap simple 5v->3.3V LDO module. There are plenty of them around, just look for "AMS1117-3.3 LDO 800MA" (for example [here](https://www.aliexpress.com/item/32922450122.html?spm=a2g0o.productlist.0.0.3a7e2ecaem569r&algo_pvid=f52e3e39-9aa4-4b91-9210-d27a42d0f9a3&algo_expid=f52e3e39-9aa4-4b91-9210-d27a42d0f9a3-0&btsid=0cea64fe-6865-4948-8788-e196db6ea69f&ws_ab_test=searchweb0_0%2Csearchweb201602_10%2Csearchweb201603_52)) . CC2538 module of my choice can be purchased on aliexpress [here](https://www.aliexpress.com/item/32880588264.html?spm=a2g0o.productlist.0.0.524e330f3GDjsD&algo_pvid=a6d79351-16aa-4ca5-b4b1-4a6e16e471c4&algo_expid=a6d79351-16aa-4ca5-b4b1-4a6e16e471c4-0&btsid=91c32439-1f9d-4f4d-8f25-a1425eb1bc31&ws_ab_test=searchweb0_0%2Csearchweb201602_10%2Csearchweb201603_52)

If you choose another CC2538 module, then you need to figure out pinout yourself. Practically, there are two most common modules, the one I used (which has PCB antenna and IPX connector for external one) and another one which has only IPX. IMPORTANT: Pinout of those modules is different.

Be aware that there is no use for USB-UART adapter, as USB is native. Trying to avoid soldering 3 resistors and 2 capacitors by connecting to the USB-UART will not work ). It is native USB. It is not UART. It is not CC2530 :)

In order to improve lattency, in zigbee2mqtt you can(and have to!) reduce delay in the queue. In configuration.yaml (at least in dev branch, and should be available in release from some version), there is a new section with new parameter:

```
 queue:
   delay: 5
```

Default delay between commands in zigbee2mqtt is 250ms. Which makes it 1 second to turn on 5 lamps. With CC2538 I am able to achieve the same over 20ms. 

Here is also information about a bit more settled schematics, PCB layout and BOM for [USB stick with this module](https://modkam.ru/?p=1112#more-1112). (Courtesy of Jager, who made it) It is in Russian, but BOM and gerber files are international :) PCB is spceicifally designed to allow flexibility. You can solder USB-A and use as stick, or can solder micro-USB and use on cable. You also have freedom to use or not external antenae. If you don't want it, do not solder connector. But keep in mind, if you use external antena, you will need to resolder one resistor on module (shown there on picture with arrow).

Keep in mind, while LEDs are in the design of schematics, current firmware doesn't use them, I am focused at the moment on principal task of getting it very right. LEDs will come as bonus (still usefull though).
There is also instruction [how to flash with J-Link](https://modkam.ru/?p=1188). It is in Russian also, but it mostly set of self-explanatory screenshoots, and almost no text :)
