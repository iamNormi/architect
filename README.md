## Architect

> Yet-Another-Arch-Installer

This project not finished, but currently a simple set of shell scripts/templated files to bootstrap an Arch Linux system. It is currently **very** minimal. By default, the script will:

- Partition a disk into two partitions:

  - `boot`: 500MiB ESP partition, formatted as FAT32
  - `root`: Size of available space on disk, formatted as Ext4

- Install very few basic packages
- Install and configure `systemd-boot`
- Configure locale/timezone/keyboard layout
- Detect requirement for, and if necessary install microcode packages
- Create a non-root user and enable `sudo` access
- Install and enable NetworkManager

## Getting Started

To use this script, boot into the Arch ISO and run:

```bash
$ curl -sLo stage1.sh https://raw.githubusercontent.com/jnsgruk/architect/master/stage1.sh
$ DISK=/dev/vda /bin/bash stage1.sh
```

Additional options can be specified as environment variables:

|     Name      |  Format  |     Default     | Comment                       |
| :-----------: | :------: | :-------------: | ----------------------------- |
| `NEWHOSTNAME` | `string` |    `archie`     | Hostname of installed system. |
|   `NEWUSER`   | `string` |      `jon`      | Non-root user to create.      |
|   `LOCALE`    | `string` |  `en_GB.UTF-8`  | Locale to use.                |
|     `TZ`      | `string` | `Europe/London` | Timezone to configure.        |
|   `KEYMAP`    | `string` |      `uk`       | Keyboard layout to configure. |

These should be prepended to the install command, as is shown with the `DISK` variable above, or sourced from a `dotenv` file.

## TODO/Contributing

Coming soon...

- Enable option settings with a JSON/YAML file
- Enable customisation of installed packages
- Presets for desktop environments:
  - Gnome
  - Plasma
  - XFCE
  - MATE
- Update disk partitioning to include:
  - LVM/LUKS with ext4
  - btrfs
  - LVM/LUKS with btrfs
- Non-EFI bootloader install with GRUB
- Install and configure `yay`
- Configure a swapfile
