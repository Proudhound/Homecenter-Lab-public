# Vendor-neutral energy model

The HomeCenter energy layer should expose neutral concepts instead of hard-wiring automation to a specific vendor.

```text
PV_SMALL
PV_ROOF
HOUSE_LOAD
GRID_IMPORT
GRID_EXPORT
BATTERY_PRIMARY_SOC
BATTERY_SECONDARY_SOC
```

This allows storage systems, inverters or PV sources to change without forcing the automation layer to be rebuilt.
