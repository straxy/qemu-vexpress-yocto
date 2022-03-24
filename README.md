# qemu-vexpress-yocto
Base repo for qemu-vexpress yocto

INSTRUCTIONS
============

1) Initialize repo

`repo init -u https://github.com/straxy/qemu-vexpress-yocto -m default.xml`

`repo sync -j4`

2) Setup environment

`source setup-environment build_fb`

3) Start build

`DISTRO=mistra-framebuffer MACHINE=vexpress-qemu bitbake core-image-test`

NOTE: Other available distro is `mistra-x11`.

Output image is in `./tmp/deploy/images/vexpress-qemu`.

4) Create an empty sd card with

`qemu-img create sd.img 1G`

5) Copy `.wic` image to sd card

`dd if=core-image-test-vexpress-qemu.wic of=sd.img bs=1M`

6) Resize image to 1GiB

`qemu-img resize sd.img 1G`

SD card is ready to use.
