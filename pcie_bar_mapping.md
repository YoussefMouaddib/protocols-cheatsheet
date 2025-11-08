# PCIe BAR Mapping Guide

## BAR Purpose
Expose regions of FPGA memory/peripherals to the host as MMIO.

## BAR Types
- 32-bit memory  
- 64-bit memory  
- IO space (deprecated)  
- Prefetchable (hint for caching)

## Flow
1. FPGA PCIe endpoint IP defines BAR sizes.  
2. Host enumerates PCIe tree → assigns addresses to BARs.  
3. OS maps BAR to virtual memory.  
4. Host software reads/writes registers in FPGA logic.

## FPGA Logic
Typically a Wishbone/AXI slave mapped behind the BAR.

## Testing
Use `lspci -vv`, `setpci`, and simple user-space mmap to poke registers.
