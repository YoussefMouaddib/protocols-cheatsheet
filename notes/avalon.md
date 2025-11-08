# Avalon (Intel/Altera)

## Purpose
Intel FPGA interconnect. Used in Qsys/Platform Designer systems.

## Signal Groups
- Address, Write Data, Read Data  
- Read/Write control  
- Waitrequest (stall)  
- Burst signals for advanced variants

## Transaction Flow
Master presents address + control. Slave may hold off using waitrequest. Data transferred when waitrequest=0.

## Strengths
- Tight integration with Intel FPGA toolchains.  
- Simple for single-master systems.  
- Optional pipelining/burst variations.

## Where LiteX Uses It
- Only used when integrating with Intel IP blocks.  
- Usually wrapped/bridged to Wishbone or AXI inside LiteX.
