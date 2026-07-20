# Ventoy: Reusable Bootable USB & DiskPart Basics

## Overview

This document explains why I switched from Rufus to Ventoy for creating bootable USB drives, how I restored a Ventoy USB back to a normal USB drive using DiskPart, and how I cleaned a heavily partitioned SSD after multiple failed operating system installations.

---

## Test System

| Component | Specification |
|-----------|---------------|
| Laptop | HP ProBook |
| Processor | Intel Core i3-2310M (2nd Generation) |
| RAM | 8 GB DDR3 |
| Storage | Samsung PM851 128 GB SSD (119 GB usable) |
| Architecture | 64-bit (x64) |
| Operating System | Windows 10 |

---

# Why I Switched from Rufus to Ventoy

I wanted to experiment with several operating systems, including:

- Xubuntu
- Linux Mint
- ChromeOS Flex
- Windows

Initially, I used **Rufus** to create bootable USB drives. Rufus works well, but every time a new operating system is prepared, the entire USB drive is rewritten.

Since I planned to install many operating systems, I looked for a more efficient solution and discovered **Ventoy**.

## Advantages of Ventoy

Unlike Rufus, Ventoy installs its bootloader only once.

After the initial installation, creating a bootable USB is as simple as copying an ISO file onto the drive.

### Example

```text
Ventoy USB
│
├── Windows11.iso
├── LinuxMint.iso
├── Fedora.iso
└── Xubuntu.iso
```

When the computer boots from the USB, Ventoy automatically detects the ISO files and lets you choose which one to launch.

### Why This Matters

- Less time creating installation media.
- Convenient for testing multiple operating systems.
- Reduces unnecessary full-drive rewrites compared to repeatedly recreating bootable media with Rufus.

---

# Restoring a Ventoy USB to a Normal USB

Windows' normal **Format** option may not completely restore a Ventoy USB because Ventoy creates multiple partitions.

I used **DiskPart** to erase the partition table and create a fresh partition.

> **Warning**
>
> These commands permanently erase the selected disk. Always verify that you have selected the correct USB drive before running `clean`.

Open **Command Prompt as Administrator**.

```cmd
diskpart
list disk
select disk X
clean
create partition primary
format fs=fat32 quick
assign
exit
```

Replace **X** with the number corresponding to your USB drive.

After these commands, the USB behaves like a normal removable drive again.

---

# Cleaning My SSD After Multiple Failed Installations

After experimenting with Xubuntu, Linux Mint, and ChromeOS Flex, several failed installation attempts left my SSD with multiple partitions. Instead of deleting each partition manually, I chose to completely erase the partition table and allow Windows Setup to recreate the required partitions automatically.

## During Windows Installation

### Accessing the Disk Selection Screen

1. Boot from the Windows installation USB.
2. Select your language and keyboard layout.
3. Click **Install Now**.
4. When prompted for the installation type, choose **Custom: Install Windows only (advanced)** instead of the upgrade option.
5. The disk selection screen will appear, showing all available drives and partitions.
6. Press **Shift + F10** to open Command Prompt.

### Cleaning the Disk

Run the following commands:

```cmd
diskpart
list disk
select disk 0
clean
exit
```

> **Important**
>
> Make sure you select the correct disk. My laptop's SSD was **Disk 0** because it matched the expected capacity of approximately **119 GB**.

### Continue the Installation

1. Close Command Prompt.
2. Click **Refresh**.
3. The drive should now appear as **Unallocated Space**.
4. Select the unallocated space and click **Next**.
5. Windows Setup will automatically create the required system partitions.

---

# Lessons Learned

## Ventoy is Excellent for Testing Multiple Operating Systems

If you frequently install different operating systems, Ventoy is significantly more convenient than recreating a bootable USB every time.

---

## DiskPart is a Powerful Recovery Tool

Learning DiskPart made it much easier to recover from installation mistakes and damaged partition layouts.

---

## Verify the Selected Disk

Running `clean` on the wrong disk will erase all data on that drive.

Always compare the reported storage size before selecting a disk.

---

## Partition Style Matters

Older systems often boot using **Legacy BIOS** with **MBR** partitioning.

Modern systems generally use **UEFI** with **GPT**, which offers better compatibility and supports larger drives.

Choosing the wrong partition style may prevent the system from booting correctly.

---
## Concepts Practiced

- Creating reusable bootable USB drives
- Managing disk partitions with DiskPart
- Preparing installation media for multiple operating systems
- Selecting appropriate partition styles (GPT and MBR)
- Understanding UEFI and Legacy BIOS compatibility
- Troubleshooting operating system installation issues
- Recovering storage devices after failed installations
  
---

**Status:** Complete

*Last Updated: July 2026*
