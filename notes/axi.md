# AXI / AXI4 / AXI4-Lite

## Purpose
AMBA AXI is Arm’s high-performance on-chip interconnect protocol. Used for CPU–memory paths, DMA engines, accelerators.

## Signal Groups
- Read Address: ARADDR, ARVALID, ARREADY, ARPROT, ARLEN, ARSIZE, ARBURST  
- Read Data: RDATA, RVALID, RREADY, RRESP, RLAST  
- Write Address: AWADDR, AWVALID, AWREADY, AWPROT, AWLEN, AWSIZE, AWBURST  
- Write Data: WDATA, WSTRB, WVALID, WREADY, WLAST  
- Write Response: BRESP, BVALID, BREADY  

AXI4-Lite removes burst-related signals (simple single-beat transactions).

## Transaction Flow
- Read: Master asserts AR* → slave accepts → slave returns RDATA until done.  
- Write: Master asserts AW* → master pushes WDATA → slave returns BRESP.

## Strengths
- High throughput, pipelined, out-of-order support.  
- Independent read/write channels → concurrency.  
- AXI4-Lite is simple and ideal for control/status registers.

## Where LiteX Uses It
- AXI bridges for CPUs (VexRiscv, LM32).  
- AXI-Lite CSR access.  
- Memory-mapped devices connected via AXI crossbars.
