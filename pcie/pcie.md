\# PCIe (LitePCIe Context)



\## Purpose

High-performance serial interconnect. LiteX wraps PCIe endpoints for DMA, high-bandwidth I/O, and host<->FPGA access.



\## Signal Groups (FPGA-side)

Depends on hard IP/soft IP implementation:

\- TLP ingress/egress  

\- DMA read/write channels  

\- AXI/Wishbone bridge signals depending on backend



\## Transaction Flow

Packet-based:

\- Memory Read/Write Requests → completions  

\- Advanced features: MSI/MSI-X, BARs, DMA engines



\## Strengths

\- Very high bandwidth (Gen2/Gen3 depending on core).  

\- Host-accessible memory windows.  

\- Industry-standard and complex.



\## Where LiteX Uses It

\- LitePCIe core for DMA, BARs, host memory windows.  

\- Bridging PCIe to Wishbone or AXI internally.



