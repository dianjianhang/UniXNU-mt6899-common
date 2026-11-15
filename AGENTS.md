# AGENTS.md — UniXNU-mt6899-common

Scope: shared MediaTek MT6899 (Dimensity 8400-Ultra) platform support for
UniXNU ports. First target board: Redmi Turbo 4 / POCO X7 Pro (rodin).

## Responsibilities

- `soc.toml` — SoC identity, data sources and selected components.
- `dts/mt6899.dtsi` — shared SoC hardware description; included by every
  board DTS using this SoC.
- `configs/mt6899.config` — SoC-level XNU kernel configuration fragment;
  referenced from `[kernel] config_fragments`.
- `patches/xnu/series` — ordered SoC-wide XNU patch series; an empty
  series is valid.
- `kits/` — shared platform operations, connected through the build
  configuration.

## Required reading before editing

- https://unixnu.com/porting/soc-support
- https://unixnu.com/porting/device-tree
- https://unixnu.com/porting/drivers
- https://unixnu.com/xnu/source-and-patches

## Rules

- Every hardware value needs an identified source (vendor DTS, kernel
  driver, firmware or a measured register read) recorded beside the value
  or in the device record.
- Do not add board wiring, partitions or device-specific drivers here;
  those belong in the device repository.
- Keep `components.include` limited to reviewed canonical catalog IDs.
