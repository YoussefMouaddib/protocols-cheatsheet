# Wishbone to AXI Bridge (W→AXI)

## Purpose
Let older LiteX peripherals (Wishbone only) be accessed from an AXI bus.

## Two Tasks
1. Convert Wishbone transactions into transactional AXI-Lite or AXI.
2. Handle backpressure and independent channel timing.

## Minimal Logic
- Capture WB ADR, WE, SEL, DAT_M when STB & CYC.
- Convert to AW/W or AR bursts on AXI.
- Wait for AXI B/R responses.
- Assert WB ACK when response arrives.

## Key Challenge
Wishbone is synchronous and tight.  
AXI is decoupled with five independent channels.  
State machines must track ongoing transactions.

## Good First Contribution
Enhance an existing LiteX bridge with cleaner burst logic or AXI-Lite specialization.
