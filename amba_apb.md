# AMBA APB (Advanced Peripheral Bus)

## Purpose
Low-power, low-complexity bus for simple peripheral registers.

## Signals
PADDR, PWDATA, PRDATA, PWRITE, PSEL, PENABLE, PREADY, PSLVERR.

## Transaction Flow
Two-phase:
1. Setup: PSEL=1, PADDR valid.  
2. Access: PENABLE=1, then read/write happens when PREADY=1.

## Strengths
- Ultra simple.  
- Perfect for register banks (UART, GPIO, timers).  
- Often built behind AXI-Lite bridges.

## Where It’s Used
- ARM microcontrollers and SoCs.  
- AXI to APB bridges in nearly every ARM design.
