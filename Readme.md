# HiLetgo ESP8266

In traditional "cheap electronics" fashion, this unit is verbosely marketed on [Amazon](https://www.amazon.com/gp/product/B010N1SPRK) as __HiLetgo 2pcs ESP8266 NodeMCU LUA CP2102 ESP-12E Internet WIFI Development Board Open source Serial Wireless Module Works Great with Arduino IDE/Micropython__.

In more helpful terms:

* ESP-12E is the SMT module on the board, which consists of an ESP8266 MCU
* CP2102 is the USB to UART chip on the board
* NodeMCU is the firmware that comes on the board, which contains and embedded LUA interpreter

# MicroPython

## Flashing MicroPython

The tutorials on the MicroPython site list a flashing command similar to the one below.  However, they did not work for me.  A helpful Amazon reviewer pointed out setting `--flash_mode dio` is required in order to correctly flash this particular board.

```
esptool.py --port /dev/ttyUSB0 --baud 115200 write_flash --flash_size=detect --flash_mode dio 0 esp8266-20171101-v1.9.3.bin
```

After that, open the serial REPL

```
screen /dev/ttyUSB0 115200
```

### Micropython REPL Keyboard Shortcuts

* Ctrl-A on a blank line will enter raw REPL mode. This is like a permanent paste mode, except that characters are not echoed back.
* Ctrl-B on a blank like goes to normal REPL mode.
* Ctrl-C cancels any input, or interrupts the currently running code.
* Ctrl-D on a blank line will do a soft reset.

```
import network
sta_if = network.WLAN(network.STA_IF); sta_if.active(True)
sta_if.connect("<AP_name>", "<password>") # Connect to an AP
sta_if.isconnected()                      # Check for successful connection
```

# Simba

## Simba Pins

These macro definitions link to the following physical pins.

[Simbda Pin Layout](https://github.com/eerimoq/simba/blob/master/src/boards/esp12e/board.h)

| Macro Definition | Linked pin      |
|------------------|-----------------|
| pin_gpio0_dev    | pin_device[0]   |
| pin_gpio2_dev    | pin_device[2]   |
| pin_gpio4_dev    | pin_device[5]   |
| pin_gpio5_dev    | pin_device[4]   |
| pin_gpio12_dev   | pin_device[12]  |
| pin_gpio13_dev   | pin_device[13]  |
| pin_gpio14_dev   | pin_device[14]  |
| pin_gpio15_dev   | pin_device[15]  |
| pin_gpio16_dev   | pin_device[16]  |
| pin_d0_dev       | pin_device[0]   |
| pin_d2_dev       | pin_device[2]   |
| pin_d4_dev       | pin_device[5]   |
| pin_d5_dev       | pin_device[4]   |
| pin_d12_dev      | pin_device[12]  |
| pin_d13_dev      | pin_device[13]  |
| pin_d14_dev      | pin_device[14]  |
| pin_d15_dev      | pin_device[15]  |
| pin_d16_dev      | pin_device[16]  |
| pin_led_dev      | pin_d2_dev      |
| pin_a0_dev       | pin_device[0]   |
| adc_0_dev        | adc_device[0]   |
| flash_0_dev      | flash_device[0] |
| ADC_PINS_MAX     | 1               |
