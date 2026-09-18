# brogue ce for void linux

void linux package template for brogue: community edition.

## prereqs

requires a working `void-packages` and `xbps-src` setup.

## install

```sh
git clone https://github.com/void-linux/void-packages.git
git clone https://github.com/fuathmhar/brogue-ce-void.git
cp -r brogue-ce-void/srcpkgs/brogue-ce void-packages/srcpkgs/
cd void-packages
./xbps-src pkg brogue-ce
sudo xbps-install --repository=hostdir/binpkgs brogue-ce
```

## source

https://github.com/tmewett/BrogueCE
