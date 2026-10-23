# Brother MFC-L3760CDW — Arch Linux packages

Packaging for the Brother MFC-L3760CDW printer and scanner on Arch Linux, plus
setup notes for the CUPS printer queue.

## Tested hardware

Tested with the Brother MFC-L3760CDW printer/scanner.

## Packages

| Directory | Package | Description |
|---|---|---|
| `printer/` | `brother-mfc-l3760cdw` 3.5.1-4 | LPR and CUPS printer drivers |
| `scanner/` | `brscan5` 1.7.0_0-1 | SANE scanner driver |
| `scanner/brscan-skey/` | `brscan-skey` 0.3.5_0-1 | Scanner S-KEY tool |

## Provenance and credits

These packages are based on the corresponding AUR packages:

- [`brother-mfc-l3760cdw`](https://aur.archlinux.org/packages/brother-mfc-l3760cdw)
  — originally maintained by **genuineparts** (Bernhard Jaud). The packaging
  also uses modified code from `brother-mfc-9335cdn` by **Leo Pham**.
- [`brscan5`](https://aur.archlinux.org/packages/brscan5) — originally
  maintained by **agsimmons0**.
- [`brscan-skey`](https://aur.archlinux.org/packages/brscan-skey) — originally
  maintained by **0x2501**.

Many thanks to the AUR maintainers and to Brother for the Linux drivers.

This repository is maintained by **Miroslav Pavleski** <miroslav@pavleski.net>.

## Building

Build each package from its directory:

```bash
(cd printer && makepkg -f)
(cd scanner && makepkg -f)
(cd scanner/brscan-skey && makepkg -f)
```

Install the resulting packages with `sudo pacman -U <package>.pkg.tar.zst`.
See `printer_install.md` for adding the CUPS printer queue.

The vendor `.deb` driver files are tracked as package sources. Build output
(`pkg/`, `src/` and `*.pkg.tar.*`) is ignored by `.gitignore`.
