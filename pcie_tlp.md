# PCIe TLP Cheat Sheet

## TLP Types
- Memory Read/Write  
- I/O Read/Write (deprecated in modern systems)  
- Configuration Read/Write  
- Completions  
- Messages (MSI, vendor-defined)

## Key Fields
Requester ID  
Completer ID  
Tag  
Address  
Byte Enables  
Length  
Attributes (no-snoop, relaxed ordering)

## Flow
FPGA endpoint receives TLP → decodes → maps to BAR → MMIO to logic.  
Host receives completion TLPs for reads.

## Strengths
- High bandwidth.  
- DMA capability.  
- Packet-based, scalable.

## Common FPGA Workflow
- Instantiate PCIe hard/soft IP.  
- Map BAR regions to your custom logic.  
- Implement read/write handling.
