# BRK Developer Package patches
This repository contains the patches that add support for OSD32MP1-BRK in OpenST Linux Developer Package

![OSD32MP1-BRK](img/OSD32MP1-BRK-Picture.png)

## Requirements
Tested on Ubuntu 16.04 LTS and 18.04 LTS

| Package | Version |
| ------- | ------- |
| Developer Package | v2.0.0 |
| SDK version | 3.1-openstlinux-5.4-dunfell-mp1-20-06-24 |
| U-Boot version | v2020.01-stm32mp |
| TF-A version | v2.2-stm32mp |
| Kernel Version | v5.4-stm32mp |
| Cube Programmer | v2.5 |

Developer Package istallation : https://wiki.st.com/stm32mpu/wiki/STM32MP1_Developer_Package

## What is on this repo?
Patch files for each component of the Developer Package are 
1. In arm-trusted-firmware-v2.2-stm32mp: 
- Patch files for compiling TF-A for OSD32MP1-BRK
- Makefile.sdk to replace Makefile.sdk for TF-A

Refer to https://community.st.com/s/question/0D53W00000HOJdOSAX for additional info on TF-A compilation issue

2. In u-boot-v2020.01-stm32mp
- Patch files for compiling Tf-A for OSD32MP1-BRK

3. In linux-v5.4-stm32mp
- Patch files for compiling kernel/device tree for OSD32MP1-BRK

4. FlashLayout_sdcard_stm32mp157c-osd32mp1-brk-trusted.tsv : Flashlayout file for Cube Prgrammer support

## TF-A Installation
Instructions here: https://wiki.st.com/stm32mpu/wiki/STM32MP1_Developer_Package#Installing_the_TF-A

Before 5.4.2: ```cp BRK_Developer_Package_patches/arm-trusted-firmware-v2.2-stm32mp/* [Developer Package directory]/stm32mp1-openstlinux-5.4-dunfell-mp1-20-06-24/sources/arm-ostl-linux-gnueabi/tf-a-stm32mp-2.2.r1-r0/```

## U-Boot Installation
Instructions here: https://wiki.st.com/stm32mpu/wiki/STM32MP1_Developer_Package#Installing_the_U-Boot

Before 5.3.2: ```cp BRK_Developer_Package_patches/u-boot-v2020.01-stm32mp/* [Developer Package directory]/stm32mp1-openstlinux-5.4-dunfell-mp1-20-06-24/sources/arm-ostl-linux-gnueabi/u-boot-stm32mp-2020.02-r0/```

## Kernel Installation
Instructions here: https://wiki.st.com/stm32mpu/wiki/STM32MP1_Developer_Package#Installing_the_Linux_kernel

Before 5.2.2: ```cp BRK_Developer_Package_patches/linux-v5.4-stm32mp/* [Developer Package directory]/stm32mp1-openstlinux-5.4-dunfell-mp1-20-06-24/sources/arm-ostl-linux-gnueabi/linux-stm32mp-5.4.31-r0/```


## Cube Programmer support
FlashLayout_sdcard_stm32mp157c-osd32mp1-brk-trusted.tsv provides support for Cube Programmer.

Procedure to flash BRK board via Starter Package:

```
cp [Developer Package directory]/stm32mp1-openstlinux-5.4-dunfell-mp1-20-06-24/sources/arm-ostl-linux-gnueabi/tf-a-stm32mp-2.2.r1-r0/build/serialboot/tf-a-stm32mp157c-osd32mp1-brk-serialboot.stm32 [Starter Package Directory]/stm32mp1-openstlinux-5.4-dunfell-mp1-20-06-24/images/stm32mp1/arm-trusted-firmware/

cp [Developer Package directory]/stm32mp1-openstlinux-5.4-dunfell-mp1-20-06-24/sources/arm-ostl-linux-gnueabi/tf-a-stm32mp-2.2.r1-r0/build/trusted/tf-a-stm32mp157c-osd32mp1-brk-trsuted.stm32 [Starter Package Directory]/stm32mp1-openstlinux-5.4-dunfell-mp1-20-06-24/images/stm32mp1/arm-trusted-firmware/

cp [Developer Package directory]/stm32mp1-openstlinux-5.4-dunfell-mp1-20-06-24/sources/arm-ostl-linux-gnueabi/u-boot-stm32mp-2020.02-r0/build-trusted/u-boot-stm32mp157c-osd32mp1-brk-trusted.stm32 [Starter Package Directory]/stm32mp1-openstlinux-5.4-dunfell-mp1-20-06-24/images/stm32mp1/bootloader/
```

Once image is flashed, you will need to copy kernel device tree into /bootfs directory. If you use a build directory, here is the command:

```
cp [Developer Package directory]/stm32mp1-openstlinux-5.4-dunfell-mp1-20-06-24/sources/arm-ostl-linux-gnueabi/linux-stm32mp-5.4.31-r0/build/arch/arm/boot/dts/stm32mp157c-osd32mp1-brk.dtb /media/[user]/bootfs
```

## How to contribute
1. Clone repo with a new branch: 
```git checkout https://github.com/octavosystems/BRK_Developer_Package_patches -b new_branch_name```
2. Change and test
3. Submit pull request

