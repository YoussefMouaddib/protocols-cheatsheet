# TileLink (TL-UL / TL-UH / TL-C)

## Purpose
RISC-V ecosystem interconnect used by SiFive and Chipyard. Designed for cache-coherent fabrics and scalable SoCs.

## Variants
- TL-UL: Uncached lightweight (MMIO–style)  
- TL-UH: Uncached heavy (high bandwidth)  
- TL-C: Cached (supports coherence messages)  

## Channel Groups (A/B/C/D/E)
Five separate channels enabling non-blocking communication:
- A: Requests  
- D: Responses  
- B/C/E: Probe and grant channels (coherence)

## Transaction Flow
Master issues A-channel request (read/write/atomic).  
Slave responds on D-channel.  
Coherent variants add snoop messaging.

## Strengths
- Scales extremely well to many cores.  
- First-class coherence support.  
- Fully non-blocking channels.

## Where It’s Used
- Rocket Chip.  
- Chipyard SoCs.  
- Berkeley-style RISC-V systems.
