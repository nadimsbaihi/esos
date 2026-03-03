# Spacemit #

## 1. 简介

ESOS(Energy Service OS) 是由进迭时空科技有限公司开发的能效管理系统，为系统提供辅助管理功能
包括如下硬件特性：

| 硬件 | 描述 |
| -- | -- |
|芯片型号| k1x |
|CPU| N308 |
|主频| 245Mhz |
|DDR | 共享AP DDR |
|SRAM | 256KB |

## 2. 编译说明

| 环境 | 说明 |
| --- | --- |
|PC操作系统|Linux|
|编译器|riscv-nuclei-elf-gcc version 10.2.0|
|构建工具|scons|

1) 下载源码

```
随SDK一起发布
```
2) 配置工程并准备env
```
    cd esos
    ./build.sh config

    INFO: prepare to config sdk ...
    All valid soc chips:
            0: n308
    Please select a chip:0
    All valid boards:
            0: k1-x
    Please select a board:0

```
3) 编译
```
    ./build.sh
```
4) 清除编译临时文件
```
    ./build.sh clean
```
5) 配置
```
    cd bsp/spacemit/
    scons --meuconfig
```
如果编译正确无误，会产生rtthread.bin、rtthread-n308.elf文件。其中rtthread-n308.elf需要copy到主系统的ramfs中供linux加载并启动运行。

## 3. elf文件存放路径
**小核系统的可执行文件(elf)是存放在ramfs中的，编译整个SDK前需要将elf文件存放到正确位置**

1)bianbu-desktop系统存放位置
```
1) 首先启动bianbu-desktop, 将rtthread-n308.elf放到/lib/firmware/esos.elf
2) 执行update-initramfs -u
3) 重启系统
```

2)bianbu-linux系统存放位置
```
buildroot-ext/board/spacemit/k1/target_overlay/lib/firmware/esos.elf
```

### 3.1 运行结果

如果编译 & 烧写无误，会在RUART0上看到RT-Thread的启动logo信息：

```
\ | /
- RT -     Thread Operating System
 / | \     4.0.4 build Oct 22 2025 14:57:47
 2006 - 2021 Copyright by rt-thread team

```

## 4. 驱动支持情况及计划

| 驱动 | 支持情况  |  备注  |
| ------ | :----:  | :------:  |
| uart | 支持 | uart0-1 |
| gpio | 支持 | / |
| pinctrl | 支持 | / |
| clk | 支持 | / |
| i2c | 支持 | i2c0 |
| spi | 支持 | spi0 |
| mailbox | 支持 | / |
| remoteproc | 支持 | / |
| pwm | 支持 | pwm0~9 |
| dma | 支持 | / |
| mmu | 不支持 | / |
| adma | 半支持 | 仅支持中断投送功能 |
| can | 半支持 | 仅支持中断投送功能 |
| ir | 半支持 | 仅支持中断投送功能 |


## 5. 联系人信息

维护人:
[zhuxianbin][4] < [xianbin.zhu@spacemit.com][5] >
