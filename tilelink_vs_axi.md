# TileLink vs AXI

## High-Level
TileLink: RISC-V ecosystem, coherence-ready, 5 channels.  
AXI: ARM ecosystem, industry-wide, 2+3 channels.

## Coherence
TileLink-C supports full coherence.  
AXI needs ACE/CHI for coherence.

## Ordering
TileLink encourages strict message ordering across independent channels.  
AXI allows more flexibility but requires more bookkeeping.

## Complexity
TileLink-C is hardest.  
AXI is easier for non-coherent systems.

## Where They Shine
TileLink: Multi-core RISC-V SoCs (Rocket, BOOM).  
AXI: Commercial SoCs, memory subsystems, accelerators.
