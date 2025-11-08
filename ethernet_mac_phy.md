# Ethernet MAC/PHY Cheat Sheet

## PHY
Handles the analog/line-level signaling on the cable.  
Protocols: MII, RMII, GMII, RGMII, SGMII.

## MAC
Digital logic: framing, CRC, padding, ARP, UDP, checksums.

## Data Flow
MAC TX → PHY TX → Cable  
Cable → PHY RX → MAC RX

## Common FPGA Setup
- Instantiate PHY interface (RGMII/GMII pins).
- Connect MAC core to internal bus (Wishbone/AXI).
- Software handles ARP/UDP stack when HW offload is minimal.

## Key Terms
- Preamble: 7 bytes of 0x55 + 1 byte SFD.  
- MTU: 1500 bytes typical.  
- CRC32: appended at frame end.
