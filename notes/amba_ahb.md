# AMBA AHB / AHB-Lite

## Purpose
Classic AMBA bus used before AXI became the standard.

## Signals
HADDR, HTRANS, HWRITE, HSIZE, HBURST, HREADY, HRDATA, HWDATA, HRESP.

## Transaction Flow
Master drives address + control.  
Slave uses HREADY to stall.  
Pipeline-friendly, supports bursts.

## Strengths
- Easier than AXI.  
- Single-master version (AHB-Lite) is simple.  
- Good for mid-performance embedded systems.

## Where It’s Used
- ARM Cortex-M microcontrollers.  
- Older SoCs or resource-constrained designs.
