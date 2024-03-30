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

## Drag Scroll Patch

The default Vial behavior for drag scrolling was a bit too limited for me. Using the Drag Scroll keycode, you can define a button that, when held, will toggle drag scroll mode. This is great, but when I'm scrolling long distances, I don't want to hold the button the whole time.

To fix this, I added a custom keycode `DRAG_SCROLL_FIX` that, when pressed, will toggle drag scroll mode until it is pressed again. For my layout, I defined a "Tap Dance" so that Ploopy Button D (from the diagram above) will enable drag scroll when held and will toggle drag scroll when tapped.

I've included those changes in this folder as a patch file. Normally I'd maintain a fork of the repo with my changes, but the QMK and VIAL repos are committed to so actively I didn't want to deal with merge conflicts and syncing the main branch. `git apply` should be able to apply the patch, but I haven't tested it.

## Compile Stock Firmware

```sh
> docker build . -t qmk:latest
> docker run --rm -it qmk:latest bash
$ qmk compile -kb ploopyco/madromys/rev1_001 -km via
```
`.uf2` will be in /root/qmk_firmware/.build/

## Compile [Vial](https://github.com/vial-kb/vial-qmk) Firmware

```sh
> docker build . -t qmk:latest
> docker run --rm -it qmk:latest bash
$ cd /root/qmk_firmware && git switch vial
$ (optionally apply drag scroll patch)
$ qmk compile -kb ploopyco/madromys/rev1_001 -km vial
```

## Flash Firmware

Put the device into bootloader mode:

1. Unplug it from your computer.
1. Hold down the Bottom Left button on the Adept.
1. Plug the Ploopy device into your computer.
1. The computer should recognise that a mass storage device was just plugged in. Once this is done, you should be able to drag and drop files onto the Ploopy device, as if the board was a USB drive.

then drag-and-drop a new `.uf2` file onto the "drive". The firmware will be installed automatically and the device will restart.

If the device is acting strange, use `flash_nuke.uf2`, then flash stock firmware.