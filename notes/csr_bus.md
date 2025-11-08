# CSR Bus (LiteX CSR)

## Purpose
LiteX internal bus for very lightweight register-mapped peripherals.

## Characteristics
- Not a real industry protocol.
- Generated automatically from Python descriptions.
- Exposes per-register read/write functions in software.

## Signals (conceptual)
CSR address  
CSR read/write strobes  
CSR read/write data  

## Strengths
- Ultra small footprint.
- Perfect for tiny peripherals.
- Simplifies software since LiteX auto-generates headers.

## Where It’s Used
- Every LiteX peripheral (UART, GPIO, SPI) exposes CSR registers.
