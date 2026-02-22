# AXI4 Handshake Cheatsheet

## The One Rule That Governs Everything

A transfer occurs **only when VALID=1 AND READY=1 on the same rising clock edge.**

### Asymmetry is intentional — and critical:
- **Sender** drives VALID. Must assert it and **hold it until READY goes high.** Cannot drop VALID early.
- **Receiver** drives READY. Can assert or deassert freely — this is backpressure.
- **VALID must never wait for READY.** If the sender stalls until the receiver is ready before asserting VALID, you get a deadlock. This is the most common AXI bug.
- **Data and address signals must remain stable** while VALID=1 and READY=0 — the transfer hasn't happened yet.

```
        ____________________________
VALID  |                            |___
              ____
READY  _______|    |_____________________

         ^
         transfer happens here (both high same cycle)
```

---

## The Five Channels

| Channel | Direction | Purpose |
|---------|-----------|---------|
| **AW** | Master → Slave | Write address + burst info |
| **W**  | Master → Slave | Write data beats (with WSTRB for byte lanes) |
| **B**  | Slave → Master | Write response (BRESP: OKAY, SLVERR, DECERR) |
| **AR** | Master → Slave | Read address + burst info |
| **R**  | Slave → Master | Read data beats + RRESP per beat |

### Ordering within a transaction:
- **Write:** AW and W are independent — W beats can arrive before or after AW. Slave waits for both. B comes after all W beats received.
- **Read:** AR → R beats. RLAST marks the final beat.
- AW and AR channels are **completely independent** — reads and writes can be in flight simultaneously.

---

## Burst Types

| Type | Address Behavior | Use Case |
|------|-----------------|----------|
| **INCR** | Increments by transfer size each beat | Cache lines, sequential memory |
| **FIXED** | Same address every beat | FIFOs, streaming peripherals |
| **WRAP** | Increments but wraps at power-of-two boundary | Cache-line-aligned refills |

**Key fields:** `AWLEN/ARLEN` = number of beats - 1 (so 0 = 1 beat, 15 = 16 beats). `AWSIZE/ARSIZE` = bytes per beat (log2).

---

## Write Response Codes (BRESP / RRESP)

| Code | Meaning |
|------|---------|
| `2'b00` OKAY | Normal success |
| `2'b01` EXOKAY | Exclusive access success |
| `2'b10` SLVERR | Slave error (address exists, but error occurred) |
| `2'b11` DECERR | Decode error (address not mapped) |

---

## Common Bugs

**Dropping VALID early** — if your master deasserts VALID before READY goes high, the transfer never happens but your master thinks it did. Silent data loss.

**Not holding data stable** — changing address or data while VALID=1 and READY=0 corrupts the transfer.

**Assuming W follows AW** — the W channel has no ordering dependency on AW. A well-designed slave buffers both independently.

**Forgetting WSTRB** — byte strobes on the W channel tell the slave which byte lanes are valid. Ignoring this corrupts partial writes.

**Missing RLAST/WLAST** — the last beat must assert LAST. Slaves and interconnects use this to close the transaction. Missing it hangs the channel.

**Deadlock from VALID waiting on READY** — see rule above. Never do this.

---

## MDIO Sidebar (PHY Management)
AXI controls your MAC. Your MAC talks to the PHY over **MDIO** (2-wire: MDC clock + MDIO data). PHY registers 0–31 are standardized — reg 0 is control, reg 1 is status (link up, speed, duplex). Auto-negotiation is handled entirely by the PHY over the wire, not the MAC.
