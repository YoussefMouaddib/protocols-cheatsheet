# AXI-Lite Interface (Your First Target)

## Purpose
Simple control/status register access. No bursts.

## Channels
- AW: address
- W: data
- B: response
- AR: address
- R: data

## Why Start With It?
- Always needed in SoC designs  
- LiteX uses many CSR/Wishbone registers  
- You can wrap existing registers with an AXI-Lite slave

## Minimal Slave Behavior
1. Capture AWADDR when AW handshake fires.
2. Capture WDATA when W handshake fires.
3. Write to target register.
4. Respond with BRESP = OKAY.
5. For reads: AR handshake → return RDATA.
