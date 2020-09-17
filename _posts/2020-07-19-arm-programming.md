---
layout: post
title:  "How to (and why you should) program for ARM"
date: 2020-07-19 19:41:00 +0100
---

ARM (Advanced RISC Machine) is a family of RISC architectures, initially developed by defunct British company Acorn Computers Ltd. and now maintained by British [Arm Holdings](https://www.arm.com/). It is one of the most influential processor architectures, along with x86 instruction set architecture by Intel.

Each CPU can have its own instruction set, that's why all these high-level programming languages: you don't have to bother with hard-to-read assembly code, you don't have to learn several processor instruction sets and you can develop cross-platform code, because compilers will handle the rest for you. However, some tasks require aggressive optimization of certain sections, or your programs may run in critical environments, so you'd like to program in assembly to have better performance or more control over the process. Or perhaps you just want to compile your C/C++ program for an ARM processor.

Here is a short guide on how you can (and why you should) start programming in C/C++ and ARM assembly for ARM-based architectures.

## How

There are two major ARM versions you should know about:
- ARMv7 is the most recent (and last) 32-bit address space ARM implementation.
- ARMv8 is the first (and currently only) 64-bit address space ARM architecture, which is also why it is also one of the most used ARM implementations. It has a 32-bit state AArch32 with backwards compatibility, as well as a 64-bit state AArch64 which is the most interesting part about ARMv8.

### ARMv8

ARMv8 in an AArch64 state is the instruction set you are most likely to find out there, as well as the one that will most likely be useful to you. First of all, you are going to need special software to compile and run code in an ARM architecture. This includes:

- **Compilers**: you will need two compilers, one for C and another for C++ (both also support assembly). We will use compilers targetting a 64-bit ARMv8 Cortex-A, little-endian CPU. The [Linaro toolchain](https://www.linaro.org/) is a free and open-source ARM toolchain, available for both Linux and Windows. It will make available compilers `aarch64-linux-gnu-gcc` and `aarch64-linux-gnu-g++` for C and C++ respectively, and they are used in ways similar to `gcc` and `g++`.
    - Under **Ubuntu/Debian**, you can run `sudo apt install aarch64-linux-gnu-gcc aarch64-linux-gnu-g++` to install the compilers.
    - Under **Microsoft Windows**, you can download the binaries from [here](https://www.linaro.org/downloads/) and then unzip them (you will probably want to add the `bin` folder inside the unzipped folder to your `PATH` so you can freely compile from anywhere the command line is without having to use the compiler full path). Choose `aarch64-elf` to target the right ARM architecture.
        - The [binaries directory](https://releases.linaro.org/components/toolchain/binaries/latest-7/aarch64-elf/) can be a bit confusing; `x86_64` can run in 64-bit Linux OS, `i686` can run in 32/64-bit Linux OS, and `i686-mingw32` can run in 32/64-bit Windows OS using the MinGW32 toolchain. Under Windows (32/64-bit) you obviously want [`i686-mingw32`](https://releases.linaro.org/components/toolchain/binaries/latest-7/aarch64-elf/gcc-linaro-7.5.0-2019.12-i686-mingw32_aarch64-elf.tar.xz).

- **Emulator**: since your CPU is not ARM-based (hence why you're going through so much to target ARM CPUs), you're going to need a piece of software that *emulates* the physical implementation of an ARM CPU. We will be using [QEMU](https://www.qemu.org/), a very simple, easy to use, fast and open-source emulator for a wide range of architectures.
    - Under **Ubuntu/Debian**, you can install QEMU by running `sudo apt install qemu` (for other Linux distributions see [this link](https://www.qemu.org/download/#linux)).
    - Under **Microsoft Windows**, you can download [binaries and installers for 32/64-bit Windows](https://www.qemu.org/download/#windows). I have not installed QEMU under Windows so you're on your own in this one.

#### Getting started

To get you started right away, check [this sample repository](https://github.com/dmfrodrigues/arm-programming-sample), and clone it using

```sh
git clone https://github.com/dmfrodrigues/arm-programming-sample.git
```

This is a short program for determining the euclidean distance between two points in the plane. We will in a first stage compile both files into their respective object files, and then link all the object files into an executable for ARM compiler architecture.

```sh
aarch64-linux-gnu-gcc -static -c main.c -o main.o           # Compile the main C file
aarch64-linux-gnu-gcc -static -c main_asm.s -o main_asm.o   # Compile the assembly file
aarch64-linux-gnu-gcc -static main.o main_asm.o -o main     # Link these two files
```

Finally, you have to start the emulator and run the resulting `main` executable

```sh
qemu-aarch64 main
```

and it will output the euclidean distance between (3, 4) and (2, 1), which is

```
3.162278
```

On a brief note, assembly files do not have universally defined extensions, but one usually either uses no extension, or uses the `.s` extension. As a way to prevent problems with object files having similar names, avoid having two files, one in C and one in assembly, with the same name (e.g. avoid having `main.c` and `main.s`, as you will probably forget and eventually have both files compile into the same object file `main.o`).

## Why

The ARM achitecture is winning the race in so many areas that one can certainly say Intel will be through hardships to recover from this. Even large companies like Apple and Microsoft have recently announced they will [further embrace ARM-based processors](https://siliconangle.com/2020/06/26/exiting-x86-apple-microsoft-embracing-arm-based-pc/). This recently-found fame of ARM is owed to a number of reasons.

### RISC vs CISC

There is an increase in interest around [reduced instruction set computer](https://en.wikipedia.org/wiki/Reduced_instruction_set_computer) (RISC) architectures like ARM, opposed to [complex instruction set computer](https://en.wikipedia.org/wiki/Complex_instruction_set_computer) (CISC) architectures like Motorola microprocessors and the famous Intel x86 architecture.

As it is known (or would be inferrable from their names), CISC architectures require larger and more complex CPUs with more transistors because CISC architectures tend to provide a vast instruction set (most of which is rarely used), while RISC architectures focus on providing the simplest instruction set to simplify CPUs and assembly programming.

### Smartphones

If you have a smartphone, it is most likely equipped with an ARM-based CPU running its OS natively.

- Samsung uses [Qualcomm Snapdragon](https://en.wikipedia.org/wiki/Qualcomm_Snapdragon) CPUs and [Exynos](https://en.wikipedia.org/wiki/Exynos) ARM-based system-on-chips.
- Apple uses [Apple Silicon](https://en.wikipedia.org/wiki/Apple_Silicon) ARM-architecture system-on-chip and system-in-package processors.
- Huawei uses Kirin CPUs via [HiSilicon](https://en.wikipedia.org/wiki/HiSilicon), all of which use ARM instruction set architectures.
- Xiaomi uses [ARM CPUs](https://www.arm.com/products/silicon-ip-cpu) directly, or [Qualcomm Snapdragon](https://en.wikipedia.org/wiki/Qualcomm_Snapdragon) CPUs using the ARM instruction set.

This is one of the reasons why the number of shipped ARM-based processors is [10 times greater](https://siliconangle.com/2020/06/26/exiting-x86-apple-microsoft-embracing-arm-based-pc/) than x86 processors.

The fact Apple is also preparing to use ARM on PC will allow using all its mobile apps on PC as well.

### Power consumption

There has been joint research between Microsoft and Qualcomm, which has in part resulted in [Microsoft Surface Pro X](https://www.microsoft.com/en-us/p/surface-pro-x/8vdnrp2m6hhc) using a Qualcomm Snapdragon CPU. Its performance reports of high battery-life are just an example of the estimated [25% of the power requirements](https://siliconangle.com/2020/06/26/exiting-x86-apple-microsoft-embracing-arm-based-pc/) of an x86 processor, mostly due to the fact ARM is RISC so it has less instructions to use power on, when opposed to a CISC architecture which requires quite a lot more power to keep all its hardware running.

### Price

Since ARM uses RISC it requires less transistors and its instructions require less complex hardware support than CISC architectures, so ARM CPUs end up being less expensive.

Also, Arm Holdings does not produce most ARM processors, as it mostly licenses ARM architectures to other manufacturers. This fact can help in reducing market prices since Intel cannot charge as much as they wish any longer and the CPU market will be much more competitive once several CPU manufacturers start producing their own ARM-based CPUs.

### Safety

The [Meltdown](https://en.wikipedia.org/wiki/Meltdown_(security_vulnerability)) and [Spectre](https://en.wikipedia.org/wiki/Spectre_(security_vulnerability)) security flaws, affecting mostly Intel processors, are still quite fresh since they were first disclosed in January 2018. These specific security flaws lead us to a more general conclusion that CPU architectures developed, maintained and manufactured by a single company like Intel are not subject to as much scrutiny as open-source/licensed, widespread architectures being developed by many companies, like ARM architectures.
