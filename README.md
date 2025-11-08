# ![StarTrekStarTrekTosGIF](https://github.com/user-attachments/assets/98d68d93-ce8a-49f2-b794-b20bfda30c84)
# ![EnginTf2GIF](https://github.com/user-attachments/assets/ad398162-c944-4d08-80c1-98999d167bb0)
# 👨🏽‍🔬 protocols-cheatsheet
# On-Chip Protocols Overview

## High-Level Summary
- AXI: High-performance, industry standard, concurrent R/W.  
- AXI-Lite: Control/status registers.  
- AHB: Legacy but still used in microcontrollers.  
- APB: Very simple MMIO peripheral bus.  
- Wishbone: Open-source workhorse; simple.  
- TileLink: Best for scalable RISC-V SoCs with coherence.  
- Avalon: Intel ecosystem only.  
- PCIe: Off-chip, packet-based, highest bandwidth.

## What to Use When
- High-performance memory paths: AXI, TL-UH.  
- Simple peripheral registers: AXI-Lite, APB, Wishbone.  
- Open-source SoCs: Wishbone and AXI bridges.  
- Multi-core RISC-V: TileLink.  
- FPGA to host: PCIe.

## Difficulty Ranking (approx)
Easiest → Hardest:
APB  
Wishbone  
AXI-Lite  
AHB  
Avalon  
AXI  
TileLink  
PCIe
