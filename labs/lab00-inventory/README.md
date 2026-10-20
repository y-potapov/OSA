# Lab 0 — Inventory your own machine

Pair: Potapov / <partner>   Driver first half: Potapov
Machine: Apple Mac, macOS
Date: 20.10.2026

## What I did
1. Found the CPU model, core count and thread count: `sysctl` and `system_profiler SPHardwareDataType`
2. Found the total memory, installed modules and speed: `system_profiler SPMemoryDataType`
3. Found the disk model, type and free space on the volume: `df -h /` and `system_profiler SPStorageDataType`
4. Found the firmware type and version: `system_profiler SPHardwareDataType`
5. Confirmed hardware virtualization is supported and enabled: `sysctl -n kern.hv_support`

## Result
| What | Value | Where I got it |
| :--- | :--- | :--- |
| CPU Model | <ваш процессор, напр. Apple M1> | `sysctl -n machdep.cpu.brand_string` |
| Core Count | <кол-во ядер, напр. 8> | `sysctl -n hw.physicalcpu` |
| Thread Count | <кол-во потоков, напр. 8> | `sysctl -n hw.logicalcpu` |
| Total Memory | <объем ОЗУ, напр. 16 GB> | `sysctl -n hw.memsize` |
| RAM Modules & Speed | <напр. Unified Memory, 0 slots> | `system_profiler SPMemoryDataType` |
| Disk Model & Type | <напр. APPLE SSD, NVMe> | `system_profiler SPStorageDataType` |
| Free Space on Volume | <свободное место, напр. 120Gi> | `df -h /` |
| Firmware Type & Version | <напр. iBoot, 10151.80.7> | `system_profiler SPHardwareDataType` |
| Hardware Virtualization | Enabled (1) | `sysctl -n kern.hv_support` |

## What did not work the first time
Standard Linux commands like `lscpu` or `lsblk` resulted in `command not found` on macOS, so I had to find and use macOS-specific commands like `sysctl` and `system_profiler`.

## Evidence
- [evidence/cpu.txt](evidence/cpu.txt) — CPU model, cores, virtualization, and firmware
- [evidence/memory.txt](evidence/memory.txt) — total memory and module configuration
- [evidence/disk.txt](evidence/disk.txt) — disk type, model, and free space on the volume
