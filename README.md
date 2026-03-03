Spacemit
1. Introduction

ESOS (Energy Service OS) is an energy efficiency management system developed by Spacemit Technology Co., Ltd. It provides auxiliary management functions for the system and features the following hardware specifications:
Hardware	Description
Chip Model	K1
CPU	N308
Frequency	245MHz
DDR	Shared AP DDR
SRAM	256KB
2. Compilation Instructions
Environment	Description
Host OS	Linux
Compiler	riscv-nuclei-elf-gcc version 10.2.0
Build Tool	scons
1) Download Source Code

The source code is released as part of the SDK.
2) Project Configuration and Environment Setup
Bash

cd esos
./build.sh config

INFO: prepare to config sdk ...
All valid soc chips:
        0: n308
Please select a chip: 0
All valid boards:
        0: k1-x
Please select a board: 0

3) Compile
Bash

./build.sh

4) Clean Build Artifacts
Bash

./build.sh clean

5) Advanced Configuration
Bash

cd bsp/spacemit/
scons --menuconfig

If the compilation is successful, rtthread.bin and rtthread-n308.elf files will be generated. The rtthread-n308.elf file needs to be copied to the main system's ramfs so that Linux can load and execute it.
3. ELF File Storage Paths

The executable file (.elf) for the little-core system is stored in the ramfs. Before compiling the entire SDK, you must place the ELF file in the correct location.
1) Path for bianbu-desktop system

    Start bianbu-desktop and place rtthread-n308.elf into /lib/firmware/esos.elf.

    Run update-initramfs -u.

    Reboot the system.

2) Path for bianbu-linux system
Plaintext

buildroot-ext/board/spacemit/k1/target_overlay/lib/firmware/esos.elf

3.1 Running Results

If compilation and flashing are successful, you will see the RT-Thread startup logo on RUART0:
Plaintext

 \ | /
- RT -     Thread Operating System
 / | \     4.0.4 build Oct 22 2025 14:57:47
 2006 - 2021 Copyright by rt-thread team

4. Driver Support Status and Roadmap
Driver	Support Status	Remarks
UART	Supported	UART0-1
GPIO	Supported	/
Pinctrl	Supported	/
CLK	Supported	/
I2C	Supported	I2C0
SPI	Supported	SPI0
Mailbox	Supported	/
Remoteproc	Supported	/
PWM	Supported	PWM0~9
DMA	Supported	/
MMU	Not Supported	/
ADMA	Partial	Interrupt delivery only
CAN	Partial	Interrupt delivery only
IR	Partial	Interrupt delivery only
5. Contact Information

Maintainer:
[Zhuxianbin] < xianbin.zhu@spacemit.com >
