Yocto settings for Raspberry Pi3
===

This repository contains my yocto build settings for Raspberry Pi3 Model B armv7 build on Yocto Rocko(2.4).

For Yocto sumo(2.5) and aarch64 building configurations, please refer [yocto-sumo](https://github.com/cosmo0920/rpi3-yocto-conf/tree/yocto-sumo) branch.

For Yocto rocko(2.4) and chromium-ozone-wayland building configurations, please refer [rocko-chromium](https://github.com/cosmo0920/rpi3-yocto-conf/tree/rocko-chromium) branch.

For building Firefox 60ESR on Wyaland/Weston with layer acceleratation and WEBRTC, current branch.


### Prerequisites

```bash
$ git clone -b rocko git://git.yoctoproject.org/poky.git poky-rocko
$ git clone -b rocko git://git.openembedded.org/meta-openembedded
$ git clone -b rocko git://git.yoctoproject.org/meta-raspberrypi
$ git clone -b firefox-60esr https://github.com/webdino/meta-browser.git
$ git clone -b jethro-14.0.1_rust_1.24.1 https://github.com/webdino/meta-rust.git
```

### Instruction

Specify MACHINE as `raspberrypi3` in `conf/local.conf`.

```conf
MACHINE ??= "raspberrypi3"
```

Then, run `source {YOCTO_ROOT_DIR}/oe-init-build-env` and `bitbake core-image-weston`.

If you want to build aarch64 on Raspberry Pi 3, please set MACHINE as `raspberrypi3-64`.

### Creating Boot Image

Writing weston image into SD card:

```
$ sudo dd if=./tmp/deploy/images/raspberrypi3/core-image-weston-raspberrypi3.rpi-sdimg of=/dev/sdX bs=4M
```

where `/dev/sdX` is the mounted SD card device.

### LICENSE

[MIT](LICENSE).
