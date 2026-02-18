# downgrade
Tiny python script to downgrade pacman packages 

## Usage
To just downgrade to previous version:
```sh
sudo downgrade bluez-utils
```

To downgrade package to specific version:
```sh
sudo downgrade waybar 0.13
```

You can also downgrade more than one package at the same time like this:
```sh
sudo downgrade linux-lts 6.1.7 linux-lts-headers 6.1.7 
```

To add downgraded [packages to ignorelist](https://wiki.archlinux.org/title/Pacman#Skip_package_from_being_upgraded) you can pass -i or --ignore flag to it, like this:
```sh
sudo downgrade --ignore swaync 0.10 waybar 0.12 
```

To remove those packages from ignorelist later, you can run: (or use -I)
```sh
sudo downgrade --ignore-remove swaync waybar
```

If you want to just see, what package versions did [pacman cache](https://wiki.archlinux.org/title/Pacman#Package_cache_directory), you can do it as following:
```sh
downgrade -g waybar swaync
```
```
/var/cache/pacman/pkg/waybar-0.13.0-1-x86_64.pkg.tar.zst
/var/cache/pacman/pkg/swaync-0.11.0-1-x86_64.pkg.tar.zst
/var/cache/pacman/pkg/waybar-0.13.0-3-x86_64.pkg.tar.zst
/var/cache/pacman/pkg/swaync-0.12.1-1-x86_64.pkg.tar.zst
/var/cache/pacman/pkg/waybar-0.14.0-1-x86_64.pkg.tar.zst
/var/cache/pacman/pkg/waybar-0.14.0-2-x86_64.pkg.tar.zst
/var/cache/pacman/pkg/swaync-0.12.2-1-x86_64.pkg.tar.zst
/var/cache/pacman/pkg/swaync-0.12.2-2-x86_64.pkg.tar.zst
/var/cache/pacman/pkg/swaync-0.12.3-1-x86_64.pkg.tar.zst
/var/cache/pacman/pkg/waybar-0.14.0-5-x86_64.pkg.tar.zst
/var/cache/pacman/pkg/waybar-0.14.0-6-x86_64.pkg.tar.zst
/var/cache/pacman/pkg/swaync-0.12.4-1-x86_64.pkg.tar.zst
/var/cache/pacman/pkg/waybar-0.15.0-1-x86_64.pkg.tar.zst
```

Additional help:
```
downgrade --help

usage: downgrade [-h] [-f] [-i] [-I PACKAGE [PACKAGE ...]] [-g PACKAGE [PACKAGE ...]] [packages ...]

Downgrade specified packages to given versions or get cached versions. Ignored packages can be found in /etc/pacman.d/blacklist.conf

positional arguments:
  packages              Packages and their versions in the format pkg version

options:
  -h, --help            show this help message and exit
  -f, --force           Downgrade package even if provided version is the same as installed
  -i, --ignore          If downgrading package, additionally adds downgraded packages to ignorelist
  -I, --ignore-remove PACKAGE [PACKAGE ...]
                        Remove provided package[s] from ignorelist
  -g, --get-cached PACKAGE [PACKAGE ...]
                        Print cached versions for the specified package[s]
```
