Yocto settings for Raspberry Pi3
===

This repository contains my yocto build settings for Raspberry Pi3 Model B armv7 build on Yocto Rocko(2.4) or above.

For Yocto rocko(2.4) and chromium-ozone-wayland building configurations, please refer [rocko-chromium](https://github.com/cosmo0920/rpi3-yocto-conf/tree/rocko-chromium) branch.

For Yocto rocko(2.4) and meta-rpi configurations, please refer [rocko-meta-rpi](https://github.com/cosmo0920/rpi3-yocto-conf/tree/rocko-meta-rpi) branch.

For Yocto rocko(2.4) or above and building Firefox 60ESR series on Wayland/Weston with layer acceleratation, WebRTC, and Quantum CSS (stylo), use current branch.

### Prerequisites

```bash
$ git clone -b rocko git://git.yoctoproject.org/poky.git poky-rocko
$ git clone -b rocko git://git.openembedded.org/meta-openembedded
$ git clone -b rocko git://git.yoctoproject.org/meta-raspberrypi
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
