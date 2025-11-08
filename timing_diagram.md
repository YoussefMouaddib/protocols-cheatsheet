# How to Read Protocol Timing Diagrams

## Basics
- Horizontal axis is time.  
- Each signal drawn as waveform.  
- Active edges/levels highlighted.

## What to Look For
1. When address becomes valid.  
2. When data is sampled.  
3. Ready/valid interaction.  
4. Wait states (stall cycles).  
5. Handshake rules.

## Example Heuristics
AXI: data transfers only when both VALID and READY are high.  
Wishbone: cycle asserted + strobe asserted + ack returned.  
APB: setup phase then access phase.

## Tips
- Track control first, data second.  
- Mark transitions with dots or ticks.  
- Always decode one channel at a time.
