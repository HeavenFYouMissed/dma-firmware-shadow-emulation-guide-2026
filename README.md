# PCIe DMA Firmware Shadow Emulation Guide 2026

**Comprehensive red team research on advanced PCIeLeech firmware customization**  
*(Screamer M.2, EnigmaX1, Artix-7 FPGAs – shadow config space, writemasks, EFUSE DNA locks, timed self-bricks, TLP optimizations & more)*

### ⚠️ DISCLAIMER ⚠️
**This repository is for educational and security research purposes ONLY.**  
The techniques documented here are intended to help anticheat developers and blue teams improve detections on real-world DMA vectors like:
- Anomalous PCIe config space behavior
- TLP pattern anomalies
- Donor device signature mismatches
- Writemask inconsistencies

**Do not use for cheating. No responsibility for misuse.** 🔴🔵

---

## Table of Contents

- [Introduction](#introduction)
- [Recommended Hardware](#recommended-hardware)
- [Tools Required](#tools-required)
- [guide](#guide-required)
- ---

## Introduction
**Comprehensive red team research on advanced PCIeLeech firmware customization**  
*(Screamer M.2, EnigmaX1, Artix-7 FPGAs – shadow config space, writemasks, EFUSE DNA locks, timed self-bricks, TLP optimizations & more)*
2026 PCIeLeech DMA firmware guide: Shadow config emulation, DNA locks, self-bricks & TLP tweaks for anticheat research (EnigmaX1/Screamer) – educational only 🔴🔵This project documents dma firmware behavior for anticheat and defensive research, this is for educational and security analysis research only. Cheaters thrive on secrecy so this breaks that cycle by making all firmware creation open knowledge. This information was gathered from publicly available sources and reverse engineered to have the best implementations of creating actual firmware thats leading as the top undetectable firmware, using m.2 and creating anticheat hell. This guide helps anticheat devs recreate firmware for analysis that is similar and can be tested, including: pcie behavior, firmware structure, dma emulation, config space, writemask, fpga project layout, tlp behavior in a simple guide that's somewhat easy to follow. Until now most dma knowledge is undocumented, scattered, half correct, intentionally obfuscated. This documentation exists because dma_based attacks are widely used in the cheating ecosystem but poorly understood by defenders. By making the behavior transparent, we aim to improve detection, reduce abuse, and support fair gameplay. 

## Recommended Hardware
which DMA card should I get? : If you want to save money, 35T. If you don't mind spending more for a faster and new DMA card, I suggest the 75T.
What Firmware do I need for my DMA card? : 35T - Squirrel, 75T - EnigmaX1.
If I have a 35T, and I buy a new card E.g(cap DMA 4th Gen), is it fine to flash the same FW? : Yes, both 35T and 4th gen cap DMA share the same prototype chip (squirrel).
What are the minimum specs I need for my second computer? : USB 3.0, at least 6GB RAM,
Why do I get Tiny PCIe TLP Algorithm when running a speed test? : This happens due to the motherboard in the main PC not liking the config space of the DMA FW.
How do I flash my FW? : If you are using 35T, use Open OCD to program and to upgrade or visit How to Flash
What donor board do I need? : Any PCIe Device technically can be used as a donor board. I wouldn't recommend using the values from an already existing PCIe Device you have on your computer. E.g. (GPU). I use an Intel Wifi 6 Ax200 card. You don't need to use this, you can use devices such as video capture cards, USB extensions, Sound Cards, SATA Expansion Cards, and so on.
What is Firmware Locking : Firmware locking refers to the process of securing the firmware on a device to prevent unauthorized access, modification, or copying
How does Firmware Locking Work? : Firmware locking works by getting the EFUSE FUSER_DNA value of the Artix7 chip from your DMA card and running a check on system bootup to check if a hard-coded(yourDNA) value is the same as your Artix7 DNA. If the DNA values match, the firmware will work, otherwise, the firmware won't work. This is intended to work for 1 person, and 1 person only since Artix7 chips have their own Unique Identifier(DNA).

## Tools Required
   Essential Tools (Your DMA Toolkit):
Vivado: The core software for development.
Arbor: Excellent for visualizing maps after scanning is complete.
TeleScan: Extremely useful for inspecting read-only/read-write bits and dumping critical information.
RW-Everything: A powerful utility for viewing I/O and MMIO, which is vital for Transmit/Receive Logic Protocol (TLP) operations.
Firmware Source Code: Specifically, the pcileech-wifi repository from GitHub.

## guide
https://docs.google.com/document/d/e/2PACX-1vTbMgXivYocBYuyranQOg3_JW53np0xtldHwhxCUrbktguYwlF0iMBBLHjw_r3mzBVtqPz2MS7IhA7f/pub
