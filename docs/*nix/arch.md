# Arch Linux

## Package Management

### Clean up the Pacman cache

#### Option 1

Run `pacman -Sc`. This cleans out the _entire_ pacman cache. This means no downgrades or recovering removed packages without re-downloading them.

#### Option 2

Use the [paccache](https://man.archlinux.org/man/paccache.8) utility script. This is a safer for managing the pacman cache. See more details [here](https://wiki.archlinux.org/title/Pacman#Cleaning_the_package_cache)

##### Examples

```shell
sudo paccache -ruk0  # Remove all cached versions of uninstalled packages
sudo paccache -rk1   # Remove cached package versions, retaining 1 past version
```
