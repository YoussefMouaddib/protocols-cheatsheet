# Where AXI Integrates Inside LiteX

## Key Places in the Codebase

### 1. `litex/soc/interconnect/axi`
Existing AXI modules, adapters, and helpers.
You will add your new standardized interface here.

### 2. `litex/soc/interconnect/wishbone2axi.py`
Shows how they wrap one bus around the other.

### 3. `litex/soc/csr`
CSR-to-Wishbone to AXI-Lite possible integration.

### 4. `litex/soc/integration/soc.py`
Where bus fabrics are constructed.

### 5. `litex/build/*`
Backends that produce Verilog.

## Why This Matters
To add "standardized AXI interface support," you must:
- Implement an AXI-Lite wrapper for peripherals  
- Add an AXI bus endpoint generator  
- Expose it through SoC integration config  
