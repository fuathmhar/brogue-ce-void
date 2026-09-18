# Brogue CE — Void Linux Package

Local Void Linux package for [Brogue: Community Edition](https://github.com/tmewett/BrogueCE).

## Build

From the `void-packages` directory:

```sh
./xbps-src pkg brogue-ce
```

The resulting package is placed in:

```text
hostdir/binpkgs/
```

## Install

Install the locally built package with:

```sh
sudo xbps-install --repository=hostdir/binpkgs brogue-ce
```

If the same version is already installed:

```sh
sudo xbps-install --repository=hostdir/binpkgs -f brogue-ce
```

## Files

The package installs:

```text
/usr/bin/brogue
/usr/share/brogue-ce/assets/icon.png
/usr/share/brogue-ce/assets/tiles.bin
/usr/share/brogue-ce/assets/tiles.png
/usr/share/applications/brogue-ce.desktop
```

The Brogue binary is compiled with:

```text
DATADIR=/usr/share/brogue-ce
```

This is important because Brogue otherwise looks for its assets relative to the current working directory.

## Wofi

The package includes:

```text
/usr/share/applications/brogue-ce.desktop
```

This allows Wofi's application launcher to discover Brogue CE.

Search for:

```text
Brogue CE
```

in Wofi.

## Updating

Brogue CE is locally packaged, so normal Void system updates do not automatically update it.

When a new upstream release is available:

1. Check the latest release:

```sh
curl -s https://api.github.com/repos/tmewett/BrogueCE/releases/latest \
    | grep '"tag_name"'
```

2. Update `version=` in `template`.

3. Update the SHA256 checksum.

4. Rebuild:

```sh
./xbps-src pkg brogue-ce
```

5. Install the new package:

```sh
sudo xbps-install \
    --repository=/home/schlafmohn/void-packages/hostdir/binpkgs \
    -f brogue-ce
```

The package revision should be incremented when changing the package recipe without changing the upstream version.

## System Updates

Normal Void updates continue to work as usual:

```sh
sudo xbps-install -Syu
```

However, this does **not** automatically check GitHub for newer Brogue CE releases or rebuild this local package.

## Removing

Remove the package normally with:

```sh
sudo xbps-remove brogue-ce
```

## Source

Upstream project:

https://github.com/tmewett/BrogueCE
