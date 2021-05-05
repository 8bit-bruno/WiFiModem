 # Simple Wifi RS232 Modem

The ‘Simple’ Wifi Modem it’s a device to connect a computer with an RS232 serial port to a telnet BBS. It does not use an analog phone line but internet through a wifi connection. Behaves like a Hayes dial-up modem, and it is designed and built for old computers; i use it with my first computer ever (still working!): a Sinclair Zx Spectrum and, being myself a retro-collector, also with a lot of other different machines (you can read about my collection on [www.museo-computer.it](https://www.museo-computer.it/).
My idea was to create a device with the same look and feel of a real modem: a lot of big, flashing, red LEDs and only a few SMD components.

**Main characteristics:**
- Emulation of a Hayes modem
- DB25 serial connector (optional external port)
- Uses 5v micro USB cable port for power
- LEDs for status, as in old modems
- Hardware flow control (partial implementation)

The software installed is a fork of Zimodem written by Bo Zimmerman
[https://github.com/bozimmerman/Zimodem](https://github.com/bozimmerman/Zimodem). 
It has just been modified to support this device.

if you don't want to build it by yourself i sold it fully assembled and tested on ebay (search for "Simple Wifi RS232 Modem") and on [Etsy](https://www.etsy.com/shop/HALsFriends). 
I build batches of that so maybe it will not be ever available.

**Using the Simple Wifi Modem**

Plug it into an RS232 DB25 port (or, through an adapter, into a 9 pin serial) and power it connecting a standard micro usb cable to a USB port capable of providing at least 100mA at 5v DC.
The device will turn on the Power LED (and CTS led if the jumper for flow control hardware is inserted).
Power on your computer and launch an ASCII terminal program and set the baud rate to 1200.
If you now type ATI you must see the welcome message.
To configure it use the command AT+CONFIG, follow the instructions and connect to a wireless router.  
When connected you can dial in to a bbs using ATDT [HOSTNAME]:[PORT]

[This is the complete list of commands available.](/commands)

**Hardware flow control**

Due to the limitations of the ESP-01 (there is only one GPIO available) having full hardware flow control support is impossible. I decided to test a partial implementation: the CTS pin will always remain high, while the RTS is connected to the GPIO2.
To use it put the jumpers on “hardware flow control” (the two pin jumper) and on the RTS side of the jumper “flow control”.
The CTS led will remain always on, the CTS led will respect the status of the RS232 pin.
In the terminal use the ATF0 command to enable the flow control (the default state is off).

**Firmware upgrade**

If needed you can upgrade the modem firmware or install whatever software you want. You can do in multiple ways. In every cases remove all the flow control jumpers: it’s better to leave GPIO2 low during these type of operations.

[These are the complete instructions to load a firmware on the Simple Wifi RS232 modem.](/FIRMWARE.md)

