---
layout: post
title:  "ARM rocks! A short guide for assembly programming"
date: 2020-07-19 19:41:00 +0100
---

ARM (Advanced RISC Machine) is a family of RISC architectures, initially developed by defunct British company Acorn Computers Ltd. and now maintained by British (Japanese-owned) [Arm Holdings](https://www.arm.com/). It is one of the most influential processor architectures, along with x86 instruction set architecture by Intel.

## How

Here is a short guide on how you can start programming in C/C++ and ARM assembly for ARM-based architectures.

TODO

## Why

The ARM achitecture is gaining ground in several areas (*ARM rocks*) for a number of reasons. Even large companies like Apple and Microsoft have recently announced they will [further embrace ARM-based processors](https://siliconangle.com/2020/06/26/exiting-x86-apple-microsoft-embracing-arm-based-pc/).

### RISC vs CISC

There is an increase in interest around [reduced instruction set computer](https://en.wikipedia.org/wiki/Reduced_instruction_set_computer) (RISC) architectures like ARM, opposed to [complex instruction set computer](https://en.wikipedia.org/wiki/Complex_instruction_set_computer) (CISC) architectures like Motorola microprocessors and the famous Intel x86 architecture.

As it is known (or would be inferrable from their names), CISC architectures require larger and more complex CPUs with more transistors because CISC architectures tend to provide a vast instruction set (most of which is rarely used), while RISC architectures focus on providing the simplest instruction set to simplify CPUs and assembly programming.

### Smartphones

If you have a smartphone, it is most likely equipped with an ARM-based CPU running its OS natively.
- Samsung uses [Exynos](https://en.wikipedia.org/wiki/Exynos) ARM-based system-on-chips.
- Apple uses [Apple Silicon](https://en.wikipedia.org/wiki/Apple_Silicon) ARM-architecture system-on-chip and system-in-package processors.
- Huawei uses Kirin CPUs via [HiSilicon](https://en.wikipedia.org/wiki/HiSilicon), all of which use ARM instruction set architectures.
- Xiaomi uses [ARM CPUs](https://www.arm.com/products/silicon-ip-cpu) directly, or [Qualcomm Snapdragon](https://en.wikipedia.org/wiki/Qualcomm_Snapdragon) CPUs using the ARM instruction set.

This is one of the reasons why the number of shipped ARM-based processors is [10 times greater](https://siliconangle.com/2020/06/26/exiting-x86-apple-microsoft-embracing-arm-based-pc/) than x86 processors. This will allow Apple to have all its mobile apps running on PC as well.

### Power consumption

There has been joint research between Microsoft and Qualcomm, which has in part resulted in [Microsoft Surface Pro X](https://www.microsoft.com/en-us/p/surface-pro-x/8vdnrp2m6hhc) using a Qualcomm Snapdragon CPU. Its performance reports of high battery-life are just an example of the estimated [25% of the power requirements](https://siliconangle.com/2020/06/26/exiting-x86-apple-microsoft-embracing-arm-based-pc/) of an x86 processor, mostly due to the fact ARM is RISC so it has less instructions to use power on, when opposed to a CISC architecture which requires quite a lot more power to keep all its hardware running.

### Price

Since ARM uses RISC it requires less transistors and its instructions require less complex hardware support than CISC architectures, so ARM CPUs end up being less expensive.

Also, Arm Holdings does not produce most ARM processors, it mostly licenses ARM architectures to other manufacturers. This fact can help in reducing market prices since Intel cannot charge as much as they wish any longer and the CPU market will be much more competitive once several CPU manufacturers start producing their own ARM-based CPUs.

### Safety

The [Meltdown](https://en.wikipedia.org/wiki/Meltdown_(security_vulnerability)) and [Spectre](https://en.wikipedia.org/wiki/Spectre_(security_vulnerability)) security flaws, affecting mostly Intel processors, are still quite fresh since they were first disclosed in January 2018. These specific security flaws lead us to a more general conclusion that CPU architectures developed, maintained and manufactured by a single company like Intel are not subject to as much scrutiny as open-source/licensed, widespread architectures being developed by many companies like ARM.
