# AXI Memory Map → AXI Stream Adapter

## Use Case
Move data from memory (AXI) into a streaming interface (AXIS).  
Ethernet transmit path uses this heavily.

## Core Behavior
1. AR handshake to request read burst.
2. Stream out RDATA beats until RLAST.
3. Assert TLAST when done.
4. Apply backpressure if TREADY = 0.

## Challenges
- Matching burst lengths to frame sizes.
- Keeping TLAST aligned.
- Handling partial frames.

## Common Structure
- Burst generator
- Data buffer FIFO
- AXIS output state machine
