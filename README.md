# Spacemit ESOS (Energy Service OS)

## 1. Introduction

**ESOS (Energy Service OS)** is an energy efficiency management system developed by Spacemit Technology Co., Ltd. It provides auxiliary management functions for the main system.

### Hardware Specifications

| Hardware   | Description      |
|------------|------------------|
| Chip Model | K1               |
| CPU        | N308             |
| Frequency  | 245 MHz          |
| DDR        | Shared AP DDR    |
| SRAM       | 256 KB           |

---

## 2. Compilation Instructions

### Build Environment

| Component   | Description                          |
|-------------|--------------------------------------|
| Host OS     | Linux                                |
| Compiler    | riscv-nuclei-elf-gcc 10.2.0          |
| Build Tool  | scons                                |

### 2.1 Download Source Code

The source code is provided as part of the SDK.

### 2.2 Project Configuration and Environment Setup

```bash
cd esos
./build.sh config 
INFO: prepare to config sdk ...
All valid soc chips:
        0: n308
Please select a chip: 0
All valid boards:
        0: k1-x
Please select a board: 0
```
### 2.3 Compile
```bash 
./build.sh clean
``` 
### 2.4 Clean Build Artifacts
```bash
./build.sh clean
```
### 2.5 Advanced Configuration
```bash
cd bsp/spacemit/
scons --menuconfig
```
If compilation is successful, the following files are generated:

rtthread.bin

rtthread-n308.elf

The file rtthread-n308.elf must be copied into the main system ramfs so that Linux can load and execute it.
## 3. Driver Support Status
| Driver     | Support Status | Remarks                 |
| ---------- | -------------- | ----------------------- |
| UART       | Supported      | UART0-1                 |
| GPIO       | Supported      |                         |
| Pinctrl    | Supported      |                         |
| CLK        | Supported      |                         |
| I2C        | Supported      | I2C0                    |
| SPI        | Supported      | SPI0                    |
| Mailbox    | Supported      |                         |
| Remoteproc | Supported      |                         |
| PWM        | Supported      | PWM0-9                  |
| DMA        | Supported      |                         |
| MMU        | Not Supported  |                         |
| ADMA       | Partial        | Interrupt delivery only |
| CAN        | Partial        | Interrupt delivery only |
| IR         | Partial        | Interrupt delivery only |

---

## 4. Contact Information

**Maintainer**
```
Zhuxianbin
[xianbin.zhu@spacemit.com](mailto:xianbin.zhu@spacemit.com)
```
