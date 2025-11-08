# ![StarTrekStarTrekTosGIF](https://github.com/user-attachments/assets/98d68d93-ce8a-49f2-b794-b20bfda30c84)
# 👨🏽‍🔬 
# Network & Bus Protocol Notes

## Ethernet PHY Interfaces

| Interface                             | Speed           | Pins | Clock            | Notes / Use                                                       |
| ------------------------------------- | --------------- | ---- | ---------------- | ----------------------------------------------------------------- |
| **MII** (Media Independent Interface) | 100 Mbps        | 16   | Separate RX/TX   | Standard for 100 Mbps PHYs. Data is 4 bits per direction.         |
| **RMII** (Reduced MII)                | 100 Mbps        | 10   | Shared           | Reduces pin count by sharing clock, simpler for small FPGAs.      |
| **GMII** (Gigabit MII)                | 1 Gbps          | 24   | Separate         | 8-bit data paths, high-speed. Usually FPGA or ASIC.               |
| **RGMII**                             | 1 Gbps          | 12   | Shared / Delayed | Reduced-pin GMII for Gigabit, edge-timed.                         |
| **SGMII / 1000BaseX**                 | 1 Gbps (serial) | 4+   | Serial           | High-speed serial interface, common in high-end SoCs or switches. |

**Key Points:**

* MII and RMII: 100 Mbps, simple PHYs, easier for learning / embedded FPGA.
* GMII / RGMII: Gigabit, more complex, relevant for high-speed networking.
* SGMII: Serialized, usually not modified at HDL level; just instantiate IP.
* Always check voltage and signaling standards when connecting PHYs to FPGA boards.

---

## Differences Between PHYs

* **Clocking:**

  * MII: separate RX/TX clocks
  * RMII/RGMII: shared clock
  * GMII: separate, higher frequency
  * SGMII: serial, internal clock recovery
* **Pin count:** Fewer pins = simpler board routing. RMII/RGMII are optimized for FPGA boards.
* **Data rates:** 100 Mbps vs 1 Gbps.
* **Use cases:**

  * Embedded FPGA: MII/RMII
  * Performance FPGA/ASIC: GMII/RGMII/SGMII
* **Timing considerations:** RGMII may require input/output delays in FPGA for proper timing alignment.

---

## AXI (Advanced eXtensible Interface)

| AXI Type        | Purpose                | Notes                                                                         |
| --------------- | ---------------------- | ----------------------------------------------------------------------------- |
| **AXI4-Lite**   | Control / status only  | Single transactions, easy to map to registers.                                |
| **AXI4**        | Full memory-mapped bus | Supports bursts, multiple outstanding transactions. Good for DMA, RAM access. |
| **AXI4-Stream** | Streaming data         | No address, just continuous data transfer. Ideal for packet or audio streams. |

**Important Signals to Know:**

| Signal | Direction      | Meaning                 |
| ------ | -------------- | ----------------------- |
| AW*    | Master → Slave | Write address channel   |
| AR*    | Master → Slave | Read address channel    |
| W*     | Master → Slave | Write data channel      |
| R*     | Slave → Master | Read data channel       |
| B*     | Slave → Master | Write response channel  |
| VALID  | Master/Slave   | Data/control valid flag |
| READY  | Master/Slave   | Data/control ready flag |

---

## LiteEth Overview

* LiteEth is a small, configurable Ethernet core written in **Migen**.
* Handles MAC (Media Access Control) layer, packet protocols, and optional PHY integration.
* Supports protocols: ARP, ICMP, UDP, and optional DHCP.
* Designed for lightweight FPGA SoCs with optional Wishbone bus connectivity.
* Can be integrated into LiteX SoCs or exported as Verilog for standard FPGA flows.
* PHY interfaces supported: MII, RMII, GMII, RGMII, SGMII.
* Optional features: UDP streaming, Etherbone, configurable MAC interface.

## LiteX Overview

* LiteX is a Python-based framework for building FPGA SoCs.
* Provides integration tools for cores like LiteEth, SDRAM, PCIe, and custom peripherals.
* Uses **Migen HDL** for core design and flexible bus management.
* Supports multiple buses: Wishbone (default), AXI (via bridges), and AXI-Stream.
* Includes simulation and testing scripts, as well as board support for various FPGAs.
* Encourages modular and parameterized core development, making it easier to reuse and extend components.

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

---

## @nonchy_architecture
