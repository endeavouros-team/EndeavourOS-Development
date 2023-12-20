![icon](https://raw.githubusercontent.com/endeavouros-team/artwork-images-logo/b53c4b90276e77d530785cb60d33c6bc3cc02f45/icons/endeavour-logo-sans-logotype.svg)

## [EndeavourOS](https://endeavouros.com)

## EndeavourOS installer

EndeavourOS is mainly developing a bootable Live-ISO.
Using calamares installer framework to get an Arch-based Desktop installed.

## Contribute to Development

We welcome contributions of all kinds, whether it's fixing a typo, providing code corrections, making suggestions, or reporting issues you come across.<br>

And indeed, by starting with a simple pull request, if you continue contributing over an extended period, you may consider joining the team to offer ongoing assistance and participate in the development of new ideas and changes for EndeavourOS. We can discuss changing your permissions.<br>

**Translations:**

For Calamares Modules and Information shown in install process:
[Calamares Translations](https://github.com/endeavouros-team/calamares/blob/calamares/data/eos/calamares-translations.txt)

For EndeavourOS Applications (welcome per example):
[EndeavourOS Apps translations](https://github.com/endeavouros-team/PKGBUILDS/tree/master/eos-translations)

**Installer (Calamares):**
Start having a look at the code and information on the calamares Repository (we do use a forked version):

[Calamares Installer](https://github.com/endeavouros-team/calamares)

**ISO build Framework:**
A hugely modified version of the original Archiso:

https://github.com/endeavouros-team/EndeavourOS-ISO

**EndeavourOS Applications:**
Have a look at the repositories:

[EndeavourOS Code Repositories](https://github.com/orgs/endeavouros-team/repositories)


**EndeavourOS ISO Features:**

We use the same base as Arch Linux for our ISO but add a live KDE Desktop session that starts upon Arch ISO boot.

The KDE live session is a fully functional desktop that includes essential tools such as the Firefox Browser, File Browser, Media Player, and a variety of additional tools for system tasks.

We do use our welcome-app to start the graphical installer [Calamares](https://calamares.io/) where you can read the latest release info and get knowledge about entirety EndeavourOS .

You can start gparted partition manager, and a selection of rescue tools, you can choose between offline install (only the same as the LiveSession: KDE Desktop) or netinstall where you can choose the Desktop-Environment you want to install, which will perform an installation directly loading everything fresh from the internet.

![calamares installer kde galileo](https://raw.githubusercontent.com/endeavouros-team/EndeavourOS-Development/main/images/livesession-kde-galileo.png)

**All that is needed to build the ISO is available here:**

[EndeavourOS-ISO](https://github.com/endeavouros-team/EndeavourOS-ISO)

Packages used for the squashfs-image and the Live-Session:

[packages.x86_64](https://github.com/endeavouros-team/EndeavourOS-ISO/blob/main/packages.x86_64)

Changes we need to implement to the squashfs-image are made with this:

[run_before_squashfs.sh](https://github.com/endeavouros-team/EndeavourOS-ISO/blob/main/run_before_squashfs.sh)


Our magic cleaner scripts work their magic, ensuring everything functions just the way we want it.

[cleaner_script.sh](https://github.com/endeavouros-team/calamares/blob/calamares/data/eos/scripts/cleaner_script.sh)

[chrooted_cleaner_script.sh](https://github.com/endeavouros-team/calamares/blob/calamares/data/eos/scripts/chrooted_cleaner_script.sh)

![calamares installer](https://raw.githubusercontent.com/endeavouros-team/EndeavourOS-Development/main/images/online-offline-welcome-kde-galileo.png)

The EndeavourOS installer setup differs in one major way from most other distros by using Calamares, specifically through the online installer setup. Unlike other distributions that utilize the ISO image, EndeavourOS installs the system fresh from scratch.

Install happens in stages:

**Offline Install Process:**

*SquashFS Image Transfer:*
        The offline installation utilizes the same squashfs image employed for the Live-Session of the ISO to transfer the system to the hard drive. This process occurs after Calamares has partitioned the disk.

*Removal of Unnecessary Apps:*
        Once the system is copied to the hard drive, packages that are exclusively required for the live session and installation process are automatically removed. This ensures a streamlined and efficient installation.

*Hardware Detection and Cleanup:*
        Post-installation, the system automatically detects the hardware in use and proceeds to remove unnecessary drivers and virtual machine packages, optimizing the system for the target environment.

*Configuration and User Setup:*
        The offline method also includes configuring the user and boot process after the partitioning is completed by Calamares.

*No Internet Connection Required:*
        Notably, this method does not necessitate an internet connection throughout the entire installation process.



**Online Install Process:**

*pacstrap Installs Base System:*
    The initial stage involves pacstrap installing the base system.

*Desktop Environment Selection:*
    Users can choose their preferred desktop environment (DE) and have the flexibility to opt-out of specific packages. Additionally, basic desktop packages are included, creating a comprehensive list for the second stage of installation.

*Hardware Detection and Cleanup:*
    Post-installation, the system automatically detects the hardware in use and proceeds to remove unnecessary drivers and virtual machine packages, optimizing the system for the target environment..

*Customization Options:*
    The online method provides the freedom to select the desired desktop environment and offers options for installing additional features such as printing support or Accessibility Tools. Furthermore, users can customize the package list by         removing individual packages as needed.

[install-scripts](https://github.com/endeavouros-team/calamares/tree/calamares/data/eos/scripts)

This method needs a working internet connection to proceed and will install the chosen DE „vanilla“ (no theming and configuration on the DE itself) as it would do on Archlinux itself. But with a minimal selection of packages to get a base Desktop to start making it your own.

The choosen DE (Desktop Environment) has deselectable groups for the EndeavourOS theming/fixes to be able to install it without our changes.

![selector](https://raw.githubusercontent.com/endeavouros-team/EndeavourOS-Development/main/images/eos-theme-deselect-kde-galileo.png)

We make desktops work smoothly on EndeavourOS with minimal tweaks to icons and themes, keeping the original experience intact.

[endeavouros-DE-fixes](https://github.com/endeavouros-team/endeavouros-DE-fixes)

## Calamares:
 <img src="https://raw.githubusercontent.com/calamares/calamares/calamares/src/branding/default/squid.png" width="150" height="150">
 
[Calamares](https://calamares.io/)

We use a customized Calamares for EndeavourOS installation. We adapt various modules to seamlessly integrate with our system, making careful configurations and developing exclusive modules like pacstrap for online installs. We modify some modules to meet our unique needs, ensuring an optimized installation experience for users.

[EndeavourOS Calamares scripts and configuration](https://github.com/endeavouros-team/calamares/tree/calamares/data/eos)

Also, both online and offline install uses the same calamares application.
We use welcome app and different settings.conf files set for both install methods.

## Dependencies:

[Calamares Dependencies](https://github.com/endeavouros-team/calamares#readme)

