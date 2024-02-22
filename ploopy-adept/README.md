# Ploopy Adept

## Button Mapping

```
+--------+    +------+ +------+    +--------+
|        |    |      | |      |    |        |
|        |    |  C   | |  D   |    |        |
|   B    |    |      | |      |    |    E   |
|        |    +------+ +------+    |        |
|        |                         |        |
|        |                         |        |
+--------+                         +--------+

+--------------+             +--------------+
|              |             |              |
|              |             |              |
|              |             |              |
|      A       |             |       F      |
|              |             |              |
|              |             |              |
|              |             |              |
+--------------+             +--------------+
```

* A - Mouse Btn1
* B - Mouse Btn4
* C - Mouse Btn5
* D - Drag Scroll
* E - Mouse Btn2
* F - Mouse Btn3

## Compile Firmware

```sh
docker build . -t qmk:latest
docker run --rm -it qmk:latest bash
root# qmk compile -kb ploopyco/madromys/rev1_001 -km via
# .uf2 in /root/qmk_firmware/.build/
```

## Flash Firmware

Put the device into bootloader mode:

1. Unplug it from your computer.
1. Hold down the Bottom Left button on the Adept.
1. Plug the Ploopy device into your computer.
1. The computer should recognise that a mass storage device was just plugged in. Once this is done, you should be able to drag and drop files onto the Ploopy device, as if the board was a USB drive.

then drag-and-drop a new `.uf2` file onto the "drive". The firmware will be installed automatically and the device will restart.

If the device is acting strange, use `flash_nuke.uf2`, then flash stock firmware.