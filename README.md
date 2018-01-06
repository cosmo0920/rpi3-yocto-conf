Yocto settings for Raspberry Pi3
===

This repository contains my yocto build settings for Raspberry Pi3 on Yocto Rocko(2.4).

### Prerequisites

```bash
$ git clone -b rocko git://git.yoctoproject.org/poky.git poky-rocko
$ git clone -b rocko git://git.openembedded.org/meta-openembedded
$ git clone -b rocko git://git.yoctoproject.org/meta-raspberrypi
```

### Instruction

Specify `raspberrypi3` in `conf/local.conf`.

```conf
MACHINE ??= "raspberrypi3"
```

Then, run `source poky-rocko/oe-init-build-env` and `bitbake core-image-weston`.

### Creating Boot Image

Creating weston image.

```
$ sudo dd if=./tmp/deploy/images/raspberrypi3/core-image-weston-raspberrypi3.rpi-sdimg of=/dev/sdX bs=4M
```

where `/dev/sdX` is mounted SD card device.

### LICENSE

[MIT](LICENSE).
