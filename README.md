# Crazyflie Firmware

## Official Build Instructions
See the [building and flashing instructions](https://www.bitcraze.io/documentation/repository/crazyflie-firmware/master/building-and-flashing/build/) in the github docs folder.


## Official Documentation

Check out the [Bitcraze crazyflie-firmware documentation](https://www.bitcraze.io/documentation/repository/crazyflie-firmware/master/) on our website.

## Custom Build Instructions

- Download the [ARM Embedded Toolchain](https://developer.arm.com/tools-and-software/open-source-software/developer-tools/gnu-toolchain/gnu-rm/downloads).
Double check the installation by running:
```shell
$ arm-none-eabi-gcc --version

arm-none-eabi-gcc.exe (GNU Arm Embedded Toolchain 9-2020-q2-update) 9.3.1 20200408 (release)
Copyright (C) 2019 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```
- Initialize the submodules for the `crazyflie-firmware/` repository
```shell
$ git submodule init
$ git submodule update
```
- In a **Windows CMD Shell** first build the target `libarm_math.a`. The ARM gcc runs much slower from a 
Windows shell, but Cygwin can't build the submodules due to relative path issues.
```shell
$ make libarm_math.a
```
- In a **Cygwin shell** (not GitBash, not MinTTY), you can now build the firmware:
```shell
$ make PLATFORM=cf2 && cp ./cf2.bin ../firmware-tools/cf2.bin
```