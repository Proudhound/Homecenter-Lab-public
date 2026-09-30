# Network architecture

## Principles
- separate daily-user, administration/development, home-server and IoT roles logically
- avoid exposing real IP, MAC or host details publicly
- create dedicated service accounts for integrations where possible
- keep secrets outside version control
- use VLANs where they add real operational or security value

```text
Internet / Router
│
├── Normal home network
├── Development / administration
├── HomeCenter server
│   ├── Proxmox
│   ├── Home Assistant OS
│   └── isolated house services
└── IoT / Smart Home
    ├── energy
    ├── sensors
    ├── cameras
    └── voice/audio
```

The exact production topology, addresses and identifiers remain private.
