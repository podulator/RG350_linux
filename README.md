# Linux kernel release 3.12.0 w/ rt patches for the RG-350 handheld

## Building

- clone this
- clone [the buildroot container](https://github.com/podulator/RG350_buildroot)
- run the container in the root of this repo
- make ARCH=mips rg350_defconfig
- make ARCH=mips CROSS_COMPILE=mipsel-linux- vmlinuz.bin

## What's the difference?

```
wget https://mirrors.edge.kernel.org/pub/linux/kernel/projects/rt/3.12/older/patch-3.12.0-rt2.patch.bz2
bzip2 -d patch-3.12.0-rt2.patch.bz2 
patch -p1 <patch-3.12.0-rt2.patch

------------

RG350_linux/arch/mips/include/asm/mach-jz4770/irq.h
#ifndef __ASM_JZ4770_IRQ_H__
#define __ASM_JZ4770_IRQ_H__

#define MIPS_CPU_IRQ_BASE 0

------------

RGG350_linux/arch/mips/kconfig
config GENERIC_ISA_DMA
	def_bool y
#	select ZONE_DMA if GENERIC_ISA_DMA_SUPPORT_BROKEN=n
#	select ISA_DMA_API
```




