# AXI vs AXI-Lite

## Purpose
Compare the full AXI4 protocol with its lightweight control-plane counterpart.

## AXI4
- Separate read/write channels.
- Burst transfers with length, size, and type.
- IDs for out-of-order completion.
- High throughput.

## AXI-Lite
- Single-beat transactions only.
- No bursts.
- No IDs.
- Designed for control/status registers.

## When to Use
AXI: DMA, memory controllers, GPU/NN accelerators.  
AXI-Lite: MMIO registers in peripherals.

## Difficulty Difference
AXI4 requires more FSMs and buffering. AXI-Lite is basically “Wishbone with ready/valid.”

