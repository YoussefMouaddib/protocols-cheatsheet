# AXI Crossbar Overview

## Purpose
Connect multiple AXI masters to multiple AXI slaves.

## Responsibilities
- Address decoding  
- Arbitration  
- Routing read/write responses  
- Maintaining ID/order rules

## Challenges
- Handling bursts crossing region boundaries  
- Backpressure between independent channels  
- Avoiding deadlocks in multi-master setups

## Relevance
LiteX already has partial AXI support; adding standardized AXI interfaces requires ensuring crossbar compatibility.
