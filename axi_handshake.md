# AXI Handshake Rules (Critical)

## Core Principle
Every channel uses VALID/READY. A transfer happens only when both are 1.

## Rules
- VALID must remain high until READY = 1.
- Data must stay stable while VALID = 1 and READY = 0.
- READY can toggle freely; masters/slaves may apply backpressure.

## Per-Channel Semantics
- AW: write address info
- W: write data (supports bursts)
- B: write response
- AR: read address info
- R: read data (supports bursts)

## Burst Notes
- INCR bursts increment address.
- FIXED bursts repeat address.
- WRAP bursts wrap around power-of-two boundaries.

## Ordering
Write address → write data beats → write response  
Read address → read data beats (RLAST marks final).

## Mistakes to Avoid
- Dropping VALID early  
- Latching data on wrong cycles  
- Mixing BURST types  
- Not handling backpressure across channels
