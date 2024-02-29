# Virtualization using the Command Line

Most of time, for common chores, we use virtual machines with a graphical user interface (GUI).
This is easier, but it's difficult to automate and to scale to many virtual machines.

In this workshop we use the [QEMU](https://www.qemu.org/) command line options

## Requirements

Make sure you have the `qemu-system-x86` and `qemu-system-arm` or equivalent packages install on your system.

The GNU toolchain (GCC, Make) is also required.
On a Debian/Ubuntu system, installing the `build-essentials` package should be enough.

## Short Intro

QEMU is an emulator that can make use the [KVM support](https://linux-kvm.org/page/Main_Page) in the Linux kernel to provide virtualization.
In essence, QEMU is a VMM (*Virtual Machine Monitor*) and KVM is the hypervisor, providing CPU and memory-level virtualization.

We use the `qemu-systemx-x86_64` or the `qemu-system-arm` commands to start virtual machines (emulated or virtualized).
In order to enable KVM support, you pass the `-enable-kvm` option:

```console
qemu-system-x86_64 ...
qemu-system-x86_64 -enable-kvm ...
```

There are two main ways to run a virtual machine:

1. Pass the kernel image to run.
   Use a QEMU boot protocol to load the kernel image and pass actions to it.

1. Pass an virtual hard disk image containing the filesystem and the kernel image and boot from that.
   The virtual disk image must be a bootable image and host the bootloader required.

## Minimalistic / Baremetal Hello World

Our goal is go boot a baremetal disk image that prints a "Hello, World!" message.
Since this is a very early on message, we will make use of early boot code instructions.

For that we follow the three tutorials here to build and run image files:

* x86_64: https://medium.com/@g33konaut/writing-an-x86-hello-world-boot-loader-with-assembly-3e4c5bdd96cf
* x86_64: https://blog.ghaiklor.com/2017/10/21/how-to-implement-your-own-hello-world-boot-loader/
* ARM: https://jasonblog.github.io/note/arm_emulation/hello_world_for_bare_metal_arm_using_qemu.html

## Run Full-Fledged OSes

Follow these instructions to run full-fledged OSes:

* Alpine x86: https://wiki.alpinelinux.org/wiki/QEMU
* Debian ARM: https://translatedcode.wordpress.com/2017/07/24/installing-debian-on-qemus-64-bit-arm-virt-board/
