# Home server platform

## Target role
A dedicated, energy-efficient x86-64 system provides the permanent 24/7 platform for HomeCenter.

```text
Dedicated home-server host
  -> Proxmox VE
     -> Home Assistant OS VM
     -> additional isolated service VMs/containers as needed
```

## Current reference class
The current lab uses a small-business-class Tiny/Mini/Micro PC with:
- Intel 8th-generation low-power desktop CPU class
- 16 GB DDR4 as starting point
- NVMe storage
- Gigabit Ethernet
- hardware virtualization support

Exact serial numbers, machine identifiers and private inventory data remain private.

## Validation checklist
- CPU and RAM verification
- storage health / SMART
- memory test
- thermal and fan stability
- LAN and USB tests
- virtualization features
- wake-on-LAN
- power-loss behavior
- recovery verification before reprovisioning
- Proxmox suitability
