# CC2538ZNP

Here is experimental coordinator firmware for CC2538+CC2592 modules.
To be used with Z2M.

Make use of native USB interface on C2538.

For programming, you will need J-link and I bellow included pinout for that for typical 20-pin interface.
You can use native segger application ("J-Flash" or "J-Flash lite") for flashing or you can flash from IAR.
Alternatively, if you don't have j-link, you can flash via any Raspberry Pi by using OpenOCD.
Once you do it - write little instruction how and I will add it here :)

This is minimal required schematics to use CC2538 (for module I use):

![alt text](https://github.com/antst/CC2538ZNP/raw/master/60423818-46deb400-9bef-11e9-8f71-8024a5a03d4e.png)

Be aware, that if you supply voltage from you USB-UART adapter, this might be not enough, as most of them can not deliver enough to supply CC2538+CC2592.

Power regulator circuit (surrounded by dashed line) can be replaced by cheap simple 5v->3.3V LDO module. There are plenty of them around, just look for "AMS1117-3.3 LDO 800MA" (for example [here](https://www.aliexpress.com/item/32922450122.html?spm=a2g0o.productlist.0.0.3a7e2ecaem569r&algo_pvid=f52e3e39-9aa4-4b91-9210-d27a42d0f9a3&algo_expid=f52e3e39-9aa4-4b91-9210-d27a42d0f9a3-0&btsid=0cea64fe-6865-4948-8788-e196db6ea69f&ws_ab_test=searchweb0_0%2Csearchweb201602_10%2Csearchweb201603_52)) . CC2538 module of my choice can be purchased on aliexpress [here](https://www.aliexpress.com/item/32880588264.html?spm=a2g0o.productlist.0.0.524e330f3GDjsD&algo_pvid=a6d79351-16aa-4ca5-b4b1-4a6e16e471c4&algo_expid=a6d79351-16aa-4ca5-b4b1-4a6e16e471c4-0&btsid=91c32439-1f9d-4f4d-8f25-a1425eb1bc31&ws_ab_test=searchweb0_0%2Csearchweb201602_10%2Csearchweb201603_52)

If you choose another CC2538 module, then you need to figure out pinout yourself. Practically, there are two most common modules, the one I used (which has PCB antenna and IPX connector for external one) and another one which has only IPX. IMPORTANT: Pinout of those modules is different.

Be aware that there is no use for USB-UART adapter, as USB is native. Trying to avoid soldering 3 resistors and 2 capacitors by connecting to the USB-UART will not work ). It is native USB. It is not UART. It is not CC2530 )
