# AmneziaWG 3 for OpenWrt MediaTek Filogic

This fork publishes AmneziaWG 3 packages for two exact official OpenWrt
firmware releases. Both builds target `mediatek/filogic` with the
`aarch64_cortex-a53` package architecture.

| Firmware | Download |
| --- | --- |
| OpenWrt 24.10.1 (`r28597-0425664679`) | [Download](../../releases/tag/v3.0.0-openwrt-24.10.1-mediatek-filogic) |
| OpenWrt 23.05.5 (`r24106-10cc5fcd00`) | [Download](../../releases/tag/v3.0.0-openwrt-23.05.5-mediatek-filogic) |

Each archive contains:

- `kmod-amneziawg`
- `amneziawg-tools`
- `luci-proto-amneziawg`
- Russian LuCI localization
- build information and SHA-256 checksums

The kernel module must match the exact OpenWrt release and kernel ABI. Do not
install it on another OpenWrt version or on a custom firmware build with a
different kernel ABI.

## Installation and upgrade

Extract the archive and copy the `.ipk` files to the device. If the old
`luci-app-amneziawg` package is installed, remove it first because it has been
replaced by `luci-proto-amneziawg` and owns the same LuCI files:

```sh
opkg remove luci-app-amneziawg
opkg install ./kmod-amneziawg_*.ipk \
  ./amneziawg-tools_*.ipk \
  ./luci-proto-amneziawg_*.ipk \
  ./luci-i18n-amneziawg-ru_*.ipk
reboot
```

The packages are built by
[the MediaTek Filogic release workflow](.github/workflows/build-filogic-release.yml)
from the current [upstream project](https://github.com/this-username-has-been-taken/amneziawg-openwrt).
