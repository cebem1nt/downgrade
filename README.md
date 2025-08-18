# downgrade
Tiny python script to downgrade pacman packages 

## Usage
To downgrade package, run script and pass package you want to downgrade with its verison, like this:
```sh
sudo downgrade waybar 0.13
```

You can also downgrade more than one package at the same time like this:
```sh
sudo downgrade linux-lts 6.1.7 linux-lts-headers 6.1.7 
```

To add downgraded packages to ignorelist (meaning next system update wont update downgraded packages) you can pass -i or --ignore argument to it, like this:
```sh
sudo downgrade --ignore swaync 0.10 waybar 0.12 
```

To remove those packages from ignorelist later, you can run:
```sh
sudo downgrade --ignore-remove swaync waybar
```

If you want to just see, what package versions did [pacman save for provided package](https://wiki.archlinux.org/title/Pacman#Package_cache_directory), you can do it as following:
```sh
downgrade -g waybar swaync
```

Additional help:
```sh
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
