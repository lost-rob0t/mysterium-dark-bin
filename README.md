# mysterium-dark-bin

Arch Linux binary package for the legacy **Mysterium Dark** desktop VPN client.

The package repacks the official upstream Debian release without modifying the
application payload. It installs the application under `/opt/MysteriumDark`,
creates `/usr/bin/mysterium-vpn-desktop`, installs the upstream desktop entry
and icons, and preserves Electron's required SUID sandbox mode.

## Install

```sh
git clone https://github.com/lost-rob0t/mysterium-dark-bin.git
cd mysterium-dark-bin
makepkg -si
```

Until the GitHub repository is published, build directly from this directory:

```sh
makepkg -si
```

## Package details

- Package: `mysterium-dark-bin`
- Upstream version: `10.17.10`
- Architecture: `x86_64`
- Provides/conflicts: `mysterium-vpn-desktop`
- Source: official upstream `.deb`

## Update

Change `pkgver`, update the `sha256sums_x86_64` value, then regenerate
`.SRCINFO`:

```sh
updpkgsums
makepkg --printsrcinfo > .SRCINFO
```

## Notes

Mysterium labels this desktop application as legacy. The package does not
replace or patch the bundled Mysterium node binaries.
