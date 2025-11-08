\# Wishbone



\## Purpose

Open-source bus standard widely used in LiteX for simple MMIO. Very easy to implement in Verilog.



\## Signal Groups

\- Address: ADR  

\- Data Write: DAT\_MOSI  

\- Data Read: DAT\_MISO  

\- Control: WE (write enable), STB (strobe), CYC (cycle)  

\- Acknowledge: ACK  

\- Optional: SEL, ERR, RTY



\## Transaction Flow

Master asserts CYC and STB, sets ADR and WE, waits for slave ACK. One transaction at a time.



\## Strengths

\- Extremely simple.  

\- Perfect for low-speed peripherals.  

\- No bursts, no reordering, minimal logic.



\## Where LiteX Uses It

\- CSR bus.  

\- Most LiteX peripherals (UART, SPI, timer, etc).  

\- Bridges from Wishbone to AXI exist inside the project.



