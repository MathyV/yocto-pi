This is just a convenience repo for me to store the configurations for my Raspberry Pi Yocto builds but feel free to use it. These are the changes I made from the default configuration:

* Build images for Raspberry Pi
* Build SDK for x86_64
* Remove temporary work
* Build with 10 concurrent tasks and 2 make threads per task
* Put the downloads outside of the build folder for easy sharing / cleaning up and avoiding multiple downloads

Currently it is targeted at v1.17 of Yocto (Dizzy)

```
git clone -b dizzy http://git.yoctoproject.org/git/poky
git clone https://github.com/agherzan/meta-raspberrypi
git clone https://github.com/MathyV/yocto-pi.git
source poky/oe-init-build-env yocto-pi
```
For creating a minimal build (replace `/dev/sdf` with your own SD card drive):
```
bitbake core-image-minimal
dd if=tmp/deploy/images/raspberrypi/core-image-minimal-raspberrypi.rpi-sdimg of=/dev/sdf
```
