# Wishbone Timing (Cycle-by-Cycle)

## Classic Cycle
Master asserts:
- CYC = 1 (transaction active)
- STB = 1 (request)
- WE = 1/0 (write/read)
- ADR, SEL, DAT_M

Slave responds:
- ACK = 1 (request accepted)
- DAT_S valid (on reads)

## Pipelined Wishbone
- Master may issue next request before ACK of previous.
- Requires registering STB and ADR safely.

## Wishbone Strengths
- Simple handshake
- Easy crossbar
- Lower overhead than AXI

## Weaknesses
- No bursts
- No transaction IDs
- Limited concurrency
