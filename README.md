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
| Cube Programmer | v2.4 |

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

## Installation
Copy contents of each folder into the respective folders:


