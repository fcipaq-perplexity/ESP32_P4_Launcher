# Pico Held 2

ESP32-P4 handheld, 720x720 MIPI-DSI panel (HD395003C30, mounted rotated 90 deg clockwise), I2S DAC with
built-in amplifier, SD card on SDMMC, GPIO buttons, battery sense. No touch, RTC or Wi-Fi radio.

One board package for both revisions (v1.3 and v1.4). They differ only in the Start/Select buttons.

| Revision | Start | Select | `PICOHELD2_REV` |
|----------|-------|--------|-----------------|
| v1.3     | GPIO35, active low | GPIO45, active high | 13 |
| v1.4     | GPIO49, analog (ADC2, above 3500) | GPIO35, active low | 14 (default) |

## Building

```
cd launcher
idf.py -B build_picoheld2_v14 -DLX_BOARD=picoheld2 -DPICOHELD2_REV=14 -p COM10 build flash
idf.py -B build_picoheld2_v13 -DLX_BOARD=picoheld2 -DPICOHELD2_REV=13 -p COM10 build flash
```

Or edit the default in `board/board_config.h` (`#define PICOHELD2_REV`). Use a separate build folder per
revision, or run `reconfigure` when you switch.

If the picture comes out upside down, build with `-DPICOHELD2_LCD_ROT=270`.

## Not exposed by bsp.h yet

Analog stick (GPIO16/17), VEXT sense (GPIO18), charger status (GPIO53), SD card detect (GPIO47).
