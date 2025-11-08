# LiteBus (LiteX internal concept)

## Purpose
LiteX abstracts multiple interconnect types internally. Not an official standard; more like a set of wrappers and adapters.

## Key Idea
Standardized record of signals representing:
- Address  
- Read/write data  
- Control strobes  
- Ready/valid-like handshake

Often generated automatically via the LiteX Python build system.

## Strengths
- Simplifies glue logic.  
- Converts between Wishbone, AXI-Lite, CSR bus, etc.  
- Makes peripheral integration easier.

## Where It’s Used
- Internally in LiteX when bridging multiple bus types.
