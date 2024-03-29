# Convert Atmel Studio Makefile to Unix format
[![Travis build status][badge-travis]][travis-build]
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=incyi_AtmelStudio_Travis-CI_Example&metric=alert_status)](https://sonarcloud.io/dashboard?id=incyi_AtmelStudio_Travis-CI_Example)  

Example of an Atmel Studio project for an ATmega328P with automated build on [Travis CI][travis-ci] (or any other Linux-based system).

Bismillah ar-Rahmaan ar-Raheem

# Documentation
At the moment this script is only tested using an Atmel Studio 7 project for an ATmega328P, but it should work for every MCU. Please let me know if you've tested it with a different version of Atmel Studio or a different MCU.

## Set up repository for Travis CI
In order to set up a repository of a Atmel Studio project for automatic builds on Travis CI the `.travis.yml` and `convertASMakefileToUnix.sh` scripts need to be present in the repository. Examples of those scripts can be found in this repository. Once those files are present in the repository, Travis CI needs to know that it has to build a project. More information on how to setup a repository with Travis CI can be found in their [Getting Started Docs][travis-getstarted].

## Atmel AVR Toolchain for Linux
In order to be able to build an Atmel Studio project on Linux, the [Atmel AVR Toolchain for Linux][atmel-toolchain] needs to be present on the system.
Linux provides these packages and they can be installed as shown below.
```shell
sudo apt-get update
sudo apt-get install binutils-avr gcc-avr avr-libc
```

## convertASMakefileToUnix script
This script converts a Atmel Studio, and thus Windows, makefile to a Linux makefile. It requires the Atmel AVR Toolchain for Linux to be installed on the system.

### Usage
```
usage: convertASMakefileToUnix.sh [-h] PROJECT_DIR

This script converts an Atmel Studio 7 makefile to a Unix format.
This way it should be possible to build the project under Unix (for example Ubuntu) using the Atmel AVR Toolchain for Linux.

positional arguments:
  PROJECT_DIR        The directory of the project.

optional arguments:
  -h,                Show this help message and exit.
```

### Example
```
lizzard@ubuntu:~/Documents/AtmelStudio_Travis-CI_Example$ ./convertMkToUnix.sh AtmelStudio_Travis-CI_Example
convertASMakefileToUnix 0.1.0 Copyright (c) 2016 Jeroen de Bruijn <vidavidorra@gmail.com>
This program comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to redistribute it under certain conditions.

TARGET_DIR: AtmelStudio_Travis-CI_Example/Debug
TARGET_MAKEFILE: AtmelStudio_Travis-CI_Example/Debug/Makefile
AVR_GCC_VERSION: 4.5.3

*** convertASMakefileToUnix has finished ***
```

# Licensing

[badge-travis]:         https://travis-ci.com/incyi/AtmelStudio_Travis-CI_Example.svg?token=GXoctkqhAbkBLipxHpR1&branch=master
[travis-build]:         https://travis-ci.com/incyi/AtmelStudio_Travis-CI_Example
[travis-ci]:            https://travis-ci.com
[travis-getstarted]:    https://docs.travis-ci.com/user/getting-started
[travis-docs]:          https://docs.travis-ci.com
[atmel-toolchain]:      http://www.atmel.com/tools/atmelavrtoolchainforlinux.aspx
