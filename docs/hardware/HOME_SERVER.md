# Home server platform

## Target role

A dedicated, energy-efficient x86-64 system provides the permanent 24/7 platform for HomeCenter.

```text
Dedicated home-server host
  -> Proxmox VE
     -> Home Assistant OS VM
     -> additional isolated service VMs/containers as needed
```

## Tested reference hardware

The current lab reference is a **Lenovo ThinkCentre M920q Tiny**. The unit was verified before reprovisioning instead of immediately overwriting the preinstalled operating system.

Verified configuration:

| Component | Tested state |
|---|---|
| CPU | Intel Core i5-8500T, 6 cores / 6 threads |
| RAM | 16 GB DDR4-2667, 1 × 16 GB |
| System storage | Samsung MZVLB256HAHQ-000L7, 256 GB NVMe |
| NVMe health | Healthy, wear indicator 0 during acceptance |
| Ethernet | Intel I219-LM Gigabit Ethernet |
| Wi-Fi | Intel Dual Band Wireless-AC 8265 |
| TPM | present, ready, enabled and activated |
| BIOS after update | M1UKT79A |
| Intel virtualization | enabled |
| VT-d | enabled |

Unique serial numbers, MAC addresses, license keys and private inventory identifiers are intentionally not published.

## Pre-Proxmox acceptance workflow

Before changing the hardware or installing Proxmox, the following sequence was used:

1. Record model, CPU, RAM layout, storage model and network adapters.
2. Verify the preinstalled Windows edition and activation state.
3. Check whether BitLocker/device encryption is active before firmware work.
4. Verify TPM state.
5. Record the existing BIOS revision.
6. Apply the vendor BIOS update while the original Windows installation is still available.
7. Verify Intel virtualization and VT-d in firmware.
8. Run a memory diagnostic.
9. Check NVMe health and temperature.
10. Only after the original system is documented, proceed to the physical storage upgrade.
11. Test onboard Ethernet before final Proxmox deployment.

This deliberately separates **acceptance** from **reprovisioning**. If a used system has a hardware fault, it should be discovered before the original installation and evidence are destroyed.

## Findings during acceptance

### Windows version string can be misleading

Some Windows queries returned the legacy text `Windows 10 Pro`, while the installed system reported `DisplayVersion 25H2` and build `26200.9457`.

For inventory purposes, the project therefore records the edition together with DisplayVersion and build instead of trusting the `ProductName` string alone.

### Virtualization WMI values can look wrong while a hypervisor is active

After Intel Virtualization Technology and VT-d were enabled in BIOS, this query still returned `False` values on the test installation:

```powershell
Get-CimInstance Win32_Processor |
  Format-List Name,VirtualizationFirmwareEnabled,VMMonitorModeExtensions,SecondLevelAddressTranslationExtensions
```

At the same time, `systeminfo` reported that a hypervisor was already detected and virtualization-based security was running. Device Guard also reported active VBS.

The acceptance decision therefore used multiple independent signals rather than a single WMI property.

### Device Guard requires the correct namespace

This fails on systems where the class is not exposed in the default CIM namespace:

```powershell
Get-CimInstance Win32_DeviceGuard
```

The working query was:

```powershell
Get-CimInstance -Namespace root\Microsoft\Windows\DeviceGuard -ClassName Win32_DeviceGuard
```

## Memory test

Windows Memory Diagnostic completed without detected errors before the machine was opened or modified.

This is useful on refurbished systems because it establishes a baseline before RAM, disks or cabling are touched.

## Storage plan

The lab uses a two-tier storage approach:

```text
256 GB NVMe
├── Proxmox VE
├── active VMs / containers
└── latency-sensitive application data

1 TB SATA HDD
├── backups
├── ISO images
├── templates
└── archive / bulk storage
```

The reused 1-TB SATA HDD was health-checked separately before installation. Because it already has substantial operating hours, it is intentionally not planned as the primary datastore for active databases or latency-sensitive VM workloads.

For the final Proxmox installation, the secondary HDD can be temporarily disconnected after its recognition test. This removes the possibility of accidentally selecting and formatting the wrong disk in the installer.

## Validation checklist

- [x] CPU and RAM verification
- [x] NVMe model and health verification
- [x] Windows activation/recovery state checked before reprovisioning
- [x] BitLocker/device-encryption state checked
- [x] TPM verified
- [x] BIOS updated
- [x] Intel virtualization enabled
- [x] VT-d enabled
- [x] memory diagnostic completed without errors
- [x] internal SATA bay/cable inspection
- [ ] suitable 7-mm SATA drive selection and joint detection test
- [ ] onboard Gigabit Ethernet link test
- [ ] USB/display tests relevant to the deployment
- [ ] thermal/fan stability test
- [ ] wake-on-LAN
- [ ] power-loss recovery behavior
- [ ] Proxmox installation
- [ ] post-install storage/network/backup baseline

The chronological acceptance log is documented under [docs/Historie/2026-09-30-thinkcentre-m920q-abnahme.md](../Historie/2026-09-30-thinkcentre-m920q-abnahme.md).


## Physical inspection and storage expansion

The top and bottom covers were removed before any storage modification.

Verified:

- original 2.5-inch bracket and SATA ribbon cable are present
- two SO-DIMM slots are present, one occupied and one free
- the 256-GB NVMe is physically present and seated correctly
- no obvious corrosion, burn marks or broken connectors were visible in the inspected areas

The available reused 2.5-inch HDD is 9.5 mm high. It does not fit the intended stock-bracket layout cleanly. Running it loose on top of motherboard components was rejected even though it would fit under the outer cover.

The stock 2.5-inch bay also competes with the PCIe expansion area. The short-term plan is therefore to use a **7-mm SATA drive** in the original bracket if a suitable tested drive is available.

The longer-term architecture keeps the Tiny focused on compute and treats bulk storage separately:

```text
Tiny host
├── NVMe -> hypervisor and active workloads
├── optional 7-mm SATA -> temporary/local secondary storage
└── PCIe -> future NIC or HBA

Separate / expanded storage
├── 3.5-inch HDDs -> preferred bulk storage
└── optional 2.5-inch bays -> SSDs / reused drives
```

For multi-disk growth, a proper HBA/SATA/SAS path or a separate storage node is preferred over a collection of independent USB-to-SATA adapters.
