# Syed's OS

Welcome to **Syed's OS**—a custom Linux-based system built from the ground up using a hand-configured kernel. This project combines a tailored kernel (Linux 4.18.5) with additional modules selected to suit modern security, networking, and performance needs. Below, you’ll find an overview of the OS, its features, and instructions to help you get started.

---

## Table of Contents
1. [Overview](#overview)
2. [Key Features](#key-features)
3. [System Requirements](#system-requirements)
4. [Bootloader Configuration](#bootloader-configuration)
5. [Kernel Configuration Highlights](#kernel-configuration-highlights)
6. [Build & Installation](#build--installation)
7. [Basic Usage](#basic-usage)
8. [Troubleshooting](#troubleshooting)
9. [Contributing](#contributing)
10. [License](#license)

---

## Overview

**Syed's OS** is a personal project intended to:
- Explore Linux kernel internals.
- Practice building an OS from scratch using a custom Linux From Scratch (LFS)-style build.
- Implement advanced kernel features (e.g., SELinux, custom network stack configurations, and more).
- Provide a minimal yet scalable environment that can grow based on specific use cases (IoT, containerized services, embedded AI, etc.).

This system boots with a **GRUB** bootloader and relies on a straightforward partition layout and root filesystem. It’s neither intended nor recommended for production systems—rather it’s a learning playground for low-level OS enthusiasts and advanced Linux users.

---

## Key Features

- **Custom Kernel 4.18.5**  
  Hand-tuned to support essential modules while removing unneeded bloat.

- **Security-Enhanced Linux (SELinux) Enabled**  
  Out of the box, SELinux is integrated to provide mandatory access controls. (It can be toggled at boot or fully disabled if desired.)

- **64-bit Architecture Support**  
  Built specifically for x86_64 with 64-bit computing in mind.

- **Ext4 Filesystem**  
  Optimized for journaling, POSIX ACL support, and high reliability.

- **Network Stack**  
  Includes support for IPv6, netfilter/iptables, NAT, and modern TCP congestion control (CUBIC).

- **Lightweight**  
  Streamlined configuration to exclude unnecessary drivers and modules, aiming for a smaller and more efficient kernel footprint.

---

## System Requirements

- **CPU**: 64-bit capable processor (x86_64).  
- **RAM**: Minimum 1 GB recommended.  
- **Storage**: At least 4 GB of space (for root filesystem, kernel, and userland).  
- **Bootloader**: GRUB or other bootloader capable of loading a 64-bit Linux kernel.  

> *Note:* Requirements can vary depending on what you install in userland.

---

## Bootloader Configuration

**Syed’s OS** uses GRUB as the default bootloader. A sample `grub.cfg` might look like this:

```cfg
set default=0
set timeout=5

menuentry "Syed's OS (Linux 4.18.5)" {
    linux   /boot/vmlinuz-syedsOS root=/dev/sda3 ro
}
