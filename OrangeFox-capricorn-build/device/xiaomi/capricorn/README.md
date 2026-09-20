TWRP device configuration for Xiaomi Mi 5s
==============

The Xiaomi Mi 5s (codenamed _"Capricorn"_) is a high-end smartphone from Xiaomi.

It was announced in September 2016. Release date was October 2016.

## Device specifications

Basic   | Spec Sheet
-------:|:-------------------------
CPU     | Quad-core (2x2.15 GHz Kryo & 2x1.6 GHz Kryo)
Chipset | Qualcomm MSM8996 Snapdragon 821
GPU     | Adreno 530
Memory  | 3/4 GB RAM
Shipped Android Version | 6.0.1
Storage | 64/128 GB
Battery | Li-Po 3200 mAh battery
Display | 1080 x 1920 pixels, 5.15 inches (~428 ppi pixel density)
Camera  | 12 MP, f/2.0, phase detection autofocus, dual-LED (dual tone) flash

## Device picture

![Xiaomi Mi 5s](https://xiaomi-mi.com/uploads/CatalogueImage/xiaomi-mi-5s-gray_14506_1475064497.jpg "Xiaomi Mi 5s in black")

## Features

Works:

- ADB
- Decryption of /data
- Screen brightness settings
- Now UI is very smooth (thanks to TWRP fix 16d831bee5a660f5ac6da0d8fff2b3ec4697d663)
- Vibration on touch (see https://gerrit.omnirom.org/#/c/android_bootable_recovery/+/31021/)
- Correct screenshot color (see https://gerrit.omnirom.org/#/c/android_bootable_recovery/+/31042/)
Finally execute these:

```
export ALLOW_MISSING_DEPENDENCIES=true
. build/envsetup.sh
lunch omni_capricorn-eng 
mka recoveryimage
```

To test it:

```
fastboot boot out/target/product/capricorn/recovery.img
```
