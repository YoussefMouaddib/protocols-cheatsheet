# AXI-Stream (AXIS) Overview

## Purpose
High-throughput, packet-oriented data movement. Perfect for Ethernet MAC paths.

## Signals
- TVALID: data valid
- TREADY: receiver ready
- TDATA: payload
- TKEEP: byte enables (optional)
- TLAST: marks end of frame
- TUSER: sideband metadata (optional)

## Key Rules
- Transfer = TVALID && TREADY.
- TDATA must remain stable while TVALID = 1 and TREADY = 0.
- TLAST must align with frame boundaries.

## Strengths
- Zero address overhead
- Ideal for streaming (video, network packets, DMA engines)
- Composable with FIFOs, packet filters, checksum engines

## Weaknesses
- No addressing or out-of-order capabilities
- Must combine with AXI4-Lite or AXI4-Full for control
