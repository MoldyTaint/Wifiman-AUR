# wifiman-desktop-bin

AUR package for [WiFiMan Desktop](https://desktop.wifiman.com/), a WiFi analysis and network insights tool by Ubiquiti.

## Installation

### From AUR (once published)

```bash
yay -S wifiman-desktop-bin
# or
paru -S wifiman-desktop-bin
```

### Manual Installation

```bash
git clone https://aur.archlinux.org/wifiman-desktop-bin.git
cd wifiman-desktop-bin
makepkg -si
```

### From this repository

```bash
git clone <your-repo-url>
cd Wifiman-AUR
makepkg -si
```

## What This Package Does

This package automatically:
- Downloads the official `.deb` package from Ubiquiti
- Extracts and repackages it for Arch Linux
- Maps Debian dependencies to Arch equivalents
- Installs the application to proper system locations

## Package Structure

- **Binary**: `/usr/bin/wifiman-desktop`
- **Application files**: `/usr/lib/wifiman-desktop/`
- **Desktop entry**: `/usr/share/applications/wifiman-desktop.desktop`
- **Icons**: `/usr/share/icons/hicolor/`

## Dependencies

- `net-tools` - Network configuration tools
- `iw` - Wireless configuration utility
- `openresolv` - DNS resolver management
- `libayatana-appindicator` - System tray support
- `webkit2gtk-4.1` - Web rendering engine
- `gtk3` - GTK toolkit

## Automatic Updates

This repository includes a GitHub Actions workflow that:
1. Checks daily for new WiFiMan Desktop releases
2. Automatically updates the PKGBUILD with new version and checksums
3. Regenerates .SRCINFO
4. Commits and pushes changes

The workflow runs daily at 00:00 UTC and can also be triggered manually.

## Publishing to AUR

To publish this package to the AUR:

1. **Create an AUR account** at https://aur.archlinux.org/register/

2. **Set up SSH key** for AUR:
   ```bash
   ssh-keygen -t ed25519 -C "your.email@example.com"
   # Add the public key to your AUR account settings
   ```

3. **Initialize AUR git remote**:
   ```bash
   git remote add aur ssh://aur@aur.archlinux.org/wifiman-desktop-bin.git
   ```

4. **Push to AUR**:
   ```bash
   git push aur main
   ```

5. **Update PKGBUILD maintainer info**:
   Edit the first line of PKGBUILD with your name and email.

## Updating the Package

When a new version is released:

1. Update `pkgver` in PKGBUILD
2. Download new .deb and calculate checksum:
   ```bash
   sha256sum wifiman-desktop-<version>-amd64.deb
   ```
3. Update `sha256sums` in PKGBUILD
4. Reset `pkgrel` to 1
5. Regenerate .SRCINFO:
   ```bash
   makepkg --printsrcinfo > .SRCINFO
   ```
6. Test build:
   ```bash
   makepkg -sf
   ```
7. Commit and push:
   ```bash
   git add PKGBUILD .SRCINFO
   git commit -m "Update to version <version>"
   git push
   git push aur main
   ```

## License

The WiFiMan Desktop application is proprietary software by Ubiquiti, Inc.
License terms: https://ui.com/legal/termsofservice

This PKGBUILD and packaging scripts are released to the public domain.

## Links

- [Official WiFiMan Desktop](https://desktop.wifiman.com/)
- [Ubiquiti](https://ui.com/)
- [AUR Package Guidelines](https://wiki.archlinux.org/title/AUR_submission_guidelines)

## Contributing

Contributions are welcome! Please open an issue or pull request if you find bugs or have improvements.
