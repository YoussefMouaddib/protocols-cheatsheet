# protocols-cheatsheet
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
