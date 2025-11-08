# LiteX Internal Architecture Flow

## Top Level
Python script describes SoC configuration (CPU, bus, peripherals).

## Generation Step
LiteX builds Migen modules → converts to Verilog.

## Bus Fabric
Usually Wishbone or CSR bus. Interconnect auto-generated.

## Peripherals
UART, GPIO, Timer, Ethernet, SDRAM, PCIe via LiteX cores.

## Build Backend
Targets vendor tools (Vivado, Quartus, Diamond, NextPNR).

## Why This Matters
When adding AXI, you insert a new bus interface layer inside this generation flow.
