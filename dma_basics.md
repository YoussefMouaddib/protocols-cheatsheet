# DMA Basics

## Purpose
Offload bulk memory transfers so the CPU doesn't copy data manually.

## Core Idea
A DMA engine reads a descriptor (src, dst, size) and performs the transfer autonomously.

## Modes
- Memory to memory
- Memory to peripheral
- Peripheral to memory
- Scatter-gather (descriptor chain)

## Key Signals (high level)
Read address  
Read data  
Write address  
Write data  
Interrupt on completion

## Strengths
- Reduces CPU load.
- Enables high-throughput peripherals (Ethernet, PCIe, SPI).

## Relevance for AXI
Most AXI-based SoCs integrate DMA via AXI master interfaces.
