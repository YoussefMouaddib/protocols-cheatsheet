# Migen Basics Cheat Sheet (Critical for LiteX Work)

## Purpose
Python DSL that generates RTL.

## Core Blocks
- Module(): container
- Signal(): wire/reg
- FSM(): state machine
- If/Else(): combinational logic
- sync / comb domains
- Instance(): instantiate raw Verilog inside Migen

## Flow
Python → Migen → Verilog → Synthesis

## Key Benefit for Contributions
You can inject new Verilog easily with Instance() while still integrating with Migen modules.
