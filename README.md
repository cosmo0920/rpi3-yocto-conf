Yocto settings for Raspberry Pi3
===

This repository contains my yocto build settings for Raspberry Pi3 Model B armv7 build on Yocto Rocko(2.4).

For Yocto sumo(2.5) and aarch64 building configurations, please refer [yocto-sumo](https://github.com/cosmo0920/rpi3-yocto-conf/tree/yocto-sumo) branch.

### Prerequisites

```bash
$ git clone -b rocko git://git.yoctoproject.org/poky.git poky-rocko
$ git clone -b rocko git://git.openembedded.org/meta-openembedded
$ git clone -b rocko git://git.yoctoproject.org/meta-raspberrypi
```

### Instruction

Specify MACHINE as `raspberrypi3` in `conf/local.conf`.

```conf
MACHINE ??= "raspberrypi3"
```

Then, run `source poky-rocko/oe-init-build-env` and `bitbake core-image-weston`.

If you want to build aarch64 on Raspberry Pi, please set MACHINE as `raspberrypi3-64`.

### Creating Boot Image

Writing weston image into SD card.

```
$ sudo dd if=./tmp/deploy/images/raspberrypi3/core-image-weston-raspberrypi3.rpi-sdimg of=/dev/sdX bs=4M
```

where `/dev/sdX` is the mounted SD card device.

### LICENSE

[MIT](LICENSE).
