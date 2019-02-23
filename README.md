Yocto settings for Raspberry Pi3
===

This repository contains my yocto build settings for Raspberry Pi3 Model B armv7 build on Yocto thud(2.6) or above.

For Yocto thud(2.6) or above and building Firefox 60ESR series on Wayland/Weston with layer acceleratation (TODO?), WebRTC, and Quantum CSS (stylo), use current branch.

### Prerequisites

```bash
$ mkdir poky-thud && cd $_
$ git clone -b thud git://git.yoctoproject.org/poky.git
$ git clone -b thud git://git.openembedded.org/meta-openembedded
$ git clone -b thud git://git.yoctoproject.org/meta-raspberrypi
$ git clone https://github.com/OSSystems/meta-browser.git
$ git clone https://github.com/meta-rust/meta-rust.git
```

### Instruction

Specify MACHINE as `raspberrypi3` in `conf/local.conf`.

```conf
MACHINE ??= "raspberrypi3"
```

Then, run `source ${YOCTO_ROOT_DIR}/oe-init-build-env` and `bitbake core-image-weston`.

If you want to build aarch64 image for Raspberry Pi 3, please set MACHINE as `raspberrypi3-64`.

### Creating Boot Image

Writing weston image into SD card:

```
$ sudo dd if=./tmp/deploy/images/raspberrypi3/core-image-weston-raspberrypi3.rpi-sdimg of=/dev/sdX bs=4M
```

where `/dev/sdX` is the mounted SD card device.

### LICENSE

[MIT](LICENSE).
