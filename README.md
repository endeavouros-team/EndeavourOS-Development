![icon](https://raw.githubusercontent.com/endeavouros-team/artwork-images-logo/b53c4b90276e77d530785cb60d33c6bc3cc02f45/icons/endeavour-logo-sans-logotype.svg)

[![Maintenance](https://img.shields.io/maintenance/yes/2025.svg)]()

## [EndeavourOS](https://endeavouros.com)

## EndeavourOS installer

EndeavourOS provides a bootable Live ISO using the Calamares Installer Framework to install an Arch-based desktop.

## Contribute to Development

We welcome any contribution! Whether it's just a simple typo correction, providing fixes for used code, making suggestions, or reporting issues you find, just create a [pull request](https://github.com/endeavouros-team/EndeavourOS-Development/pulls).\
If you continue contributing over time, consider joining the team to help with the ongoing development of new ideas and changes for EndeavourOS. Let us know, and we can discuss adjusting your permissions to allow you to do so.

**Translations:**

For Calamares modules and information shown during the installation process:
[Calamares Translations](https://github.com/endeavouros-team/calamares/blob/calamares/data/eos/calamares-translations.txt)

For EndeavourOS applications (e.g. Welcome):
[EndeavourOS Apps Translations](https://github.com/endeavouros-team/PKGBUILDS/tree/master/eos-translations)

**Installer (Calamares):**

Begin by taking a look at the code and information on the Calamares repository (note that we use a forked version):
[Calamares Installer](https://github.com/endeavouros-team/calamares)

**ISO Build Framework:**

A significantly modified version of the original Archiso:
[EndeavourOS ISO](https://github.com/endeavouros-team/EndeavourOS-ISO)

**EndeavourOS Applications:**

Take a look at the repositories:
[EndeavourOS Code Repositories](https://github.com/orgs/endeavouros-team/repositories)

**EndeavourOS ISO Features:**

We use the same base as Arch Linux for the ISO, but we implement a live desktop session with KDE Plasma that starts upon booting the Arch ISO.

The KDE Plasma live session provides a fully functional desktop enviroment with everything you need, including Firefox, File Browser, Media Player, and various of other tools for system tasks.

We use our Welcome app to start the graphical installer, [Calamares](https://calamares.io/), where you can read the latest release information and learn more about EndeavourOS.

You can start GParted, KDE Partition Manager (KPMcore) and a selection of rescue tools. You can choose between offline install, which installs the same KDE Plasma Desktop as the live session, or a netinstall, where you can select the desktop environment you want. The netinstall option will perform an installation by downloading everything fresh from the internet.
![calamares installer kde galileo](https://raw.githubusercontent.com/endeavouros-team/EndeavourOS-Development/main/images/livesession-kde-galileo.png)

**Everything needed to build the ISO is available here:**

[EndeavourOS-ISO](https://github.com/endeavouros-team/EndeavourOS-ISO)

Packages used for the squashfs-image and the live session:

[packages.x86_64](https://github.com/endeavouros-team/EndeavourOS-ISO/blob/main/packages.x86_64)

Changes we need to implement to the squashfs-image are made with this:

[run_before_squashfs.sh](https://github.com/endeavouros-team/EndeavourOS-ISO/blob/main/run_before_squashfs.sh)

Our magic cleaner_scripts doing some magic we need to get all working as we want:

[cleaner_script.sh](https://github.com/endeavouros-team/calamares/blob/calamares/data/eos/scripts/cleaner_script.sh)

[chrooted_cleaner_script.sh](https://github.com/endeavouros-team/calamares/blob/calamares/data/eos/scripts/chrooted_cleaner_script.sh)

![calamares installer](https://raw.githubusercontent.com/endeavouros-team/EndeavourOS-Development/main/images/online-offline-welcome-kde-galileo.png)

The EndeavourOS installer setup differs from most other distros using Calamares in one major way: it uses an online installer setup. Instead of relying on an ISO image, it installs the system fresh from scratch directly from the internet.

Install happens in stages:

**Offline Install:**

* The same system image used to load the ISO live-environment Desktop will be copied to the target.

* Packages that are only needed for the live session and installation process are removed from the target.

* After installation is finished, the system detects the hardware used and removes any unnecessary drivers and virtual machine packages.
    
The offline install uses the same squashfs image from the live session of the ISO to copy the system to your HD. Unneeded applications are then removed, and user and boot configurations are set up after Calamares partitions the disk.

This method does not require an internet connection.

**Online Install**

* Pacstrap installs the base system.
    
* User selects the DE (Desktop Environment), opts out of certain packages, and includes basic desktop packages, creating a list of packages to be installed in the second stage.
    
* After installation is finished, the system detects the hardware used and removes any unnecessary drivers and virtual machine packages.

The online method lets you choose your Desktop environment, install printing support or accessibility tools, and remove individual packages from the list if desired.

[Install-scripts](https://github.com/endeavouros-team/calamares/tree/calamares/data/eos/scripts)

This method requires a working internet connection to proceed and will install the chosen DE "vanilla" (no theming and configuration on the DE itself) similar to how it would be installed on Arch Linux. But with a minimal selection of packages to get a base desktop to start making it your own.

The chosen DE includes deselectable groups for the EndeavourOS theming/fixes, allowing you to install it without our changes.

![selector](https://raw.githubusercontent.com/endeavouros-team/EndeavourOS-Development/main/images/eos-theme-deselect-kde-galileo.png)

DEs are primiarly configured to work properly by default, with only minimal changes made to the icons and themeing in certain cases:

[EndeavourOS-DE-fixes](https://github.com/endeavouros-team/endeavouros-DE-fixes)

**Installer Options**
1. You can select between systemd-boot (default selected option), GRUB, or opt not to install a bootloader if you prefer to use your own.
2. Choose between the automatic partitioning option with presets or manual partitioning, where you can set up and mount partitions as you prefer. For manual partitioning, if you select systemd-boot, you need to set the ESP mount point to `/efi`. If you use GRUB as the bootloader, set the mount point to `/boot/efi`.

![bootloader](https://github.com/endeavouros-team/EndeavourOS-Development/assets/16797647/120fc78b-4dfb-44a9-8fba-6ca064b87f57)

## Calamares:
 <img src="https://raw.githubusercontent.com/calamares/calamares/calamares/src/branding/default/squid.png" width="150" height="150">
 
[Calamares](https://calamares.io/)

We use our own fork of Calamares. Some modules are used as-is but configured to work for EndeavourOS install, while others are created on our own, like the pacstrap module used for the online install option. Additionally, some modules are modified to meet our specific requirements for setting up EndeavourOS.

[EndeavourOS Calamares scripts and configuration](https://github.com/endeavouros-team/calamares/tree/calamares/data/eos)

Also, both online and offline installs use the same Calamares application.
However, we use the welcome app and different `settings.conf` files to configure both install methods.

## Dependencies:

[Calamares Dependencies](https://github.com/endeavouros-team/calamares#readme)


