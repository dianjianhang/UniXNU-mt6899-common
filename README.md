# UniXNU-mt6899-common

Shared SoC support for **MediaTek Dimensity 8400-Ultra (MT6899)** under
[UniXNU](https://unixnu.com).

> **Status: scaffold.** No hardware-verified values yet. Every
> `REQUIRED_` / TODO value must be derived from the vendor DTB, kernel
> sources and firmware, reviewed against an identified source, and then
> verified on hardware before the first build.

## Scope

- `dts/mt6899.dtsi` — shared SoC hardware description (CPU topology,
  interrupt controller, timers, IOMMU, shared peripherals)
- `configs/mt6899.config` — SoC-level XNU kernel configuration fragment
- `patches/xnu/series` — ordered SoC-wide XNU patch series
- `kits/` — shared platform operations selected by boards

Board wiring, memory, partitions, display, touch and other device drivers
live in the device repository (e.g. `UniXNU-rodin` for Redmi Turbo 4 /
POCO X7 Pro).

## Layout

```
UniXNU-mt6899-common/
  AGENTS.md
  README.md
  soc.toml
  configs/mt6899.config
  dts/mt6899.dtsi
  patches/xnu/series
  kits/
```

## Usage

Pin this repository in a device's `feeds.toml`:

```toml
[[source]]
name = "mt6899"
kind = "soc"
git = "https://github.com/<owner>/UniXNU-mt6899-common"
commit = "<reviewed 40-character commit>"
```

and set `soc = "mt6899"` / `soc_source = "mt6899"` in `board.toml`.

## References

- https://unixnu.com/porting/soc-support
- https://unixnu.com/porting/device-tree
- https://unixnu.com/porting/drivers

License: BSD-2-Clause-Patent (match the UniXNU base repositories).
