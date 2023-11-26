![icon](https://raw.githubusercontent.com/endeavouros-team/artwork-images-logo/b53c4b90276e77d530785cb60d33c6bc3cc02f45/icons/endeavour-logo-sans-logotype.svg)

## [EndeavourOS](https://endeavouros.com)

## EndeavourOS installer

EndeavourOS is mainly developing a bootable Live-ISO.
Using calamares installer framework to get an Archbased Desktop installed.

## Contribute to Development

We do welcome any contribution, be it only correcting a typo or providing fixes for used code, making siuggestions, reporting issues you find.<br>
And indeed simple start doing a pull request, if you start contributing over a longer period, you may want to join the team to provide constant help and join development of new ideas and changes for EndeavourOS?, we can discuss changing your permissions.<br>

**Translations:**

For Calamares Modules and Information shown in install process:
[Calamares Translations](https://github.com/endeavouros-team/calamares/blob/calamares/data/eos/calamares-translations.txt)

For EndeavourOS Applciations (welcome per example):
[EndeavourOS Apps translations](https://github.com/endeavouros-team/PKGBUILDS/tree/master/eos-translations)

**Installer (Calamares):**
Start having a look at the code and information on the calamares Repository (we do use a forked version):

[Calamares Installer](https://github.com/endeavouros-team/calamares)

**ISO build Framework:**
A hugely modified version of the original Archiso:

https://github.com/endeavouros-team/EndeavourOS-ISO

**EndeavourOS Applications:**
Have have a look at the repositories:

[EndeavourOS Code Repositories](https://github.com/orgs/endeavouros-team/repositories)


**EndeavourOS ISO Features:**

we do use the same base as Archlinux itself is using for the ISO, but we implement a live Desktop session with KDE starting on Arch-ISO boot.

The KDE live session is a fully working Desktop with all you need, Firefox Browser, Filebrowser, Mediaplayer, and extra many tools for system tasks.

We do use our welcome-app to start the graphical installer [Calamares](https://calamares.io/) where you can read the latest release Info and get knowledge around EndeavourOS at all.

You can start gparted partition manager, and a selection of rescue tools, you can choose between offline install (only the same as the LiveSession: KDE Desktop) or netinstall where you can choose the Desktop-Environment you want to install, what will perform an installation directly loading everything fresh from the internet.
![calamares installer kde galileo](https://raw.githubusercontent.com/endeavouros-team/EndeavourOS-Development/main/images/livesession-kde-galileo.png)

**All that is needed to build the ISO is available here:**

[EndeavourOS-ISO](https://github.com/endeavouros-team/EndeavourOS-ISO)

Packages used for the squashfs-image and the Live-Session:

[packages.x86_64](https://github.com/endeavouros-team/EndeavourOS-ISO/blob/main/packages.x86_64)

Changes we need to implement to the squashfs-image are made with this:

[run_before_squashfs.sh](https://github.com/endeavouros-team/EndeavourOS-ISO/blob/main/run_before_squashfs.sh)


Our magic cleaner_scripts doing some magic we need to get all working as we want:

[cleaner_script.sh](https://github.com/endeavouros-team/calamares/blob/calamares/data/eos/scripts/cleaner_script.sh)

[chrooted_cleaner_script.sh](https://github.com/endeavouros-team/calamares/blob/calamares/data/eos/scripts/chrooted_cleaner_script.sh)

![calamares installer](https://raw.githubusercontent.com/endeavouros-team/EndeavourOS-Development/main/images/online-offline-welcome-kde-galileo.png)

The EndeavourOS installer setup differs in one Major way too most other Distros using Calamares and this is the online installer setup.
As it is not using the ISO image at all and installs the system fresh from scratch.

Install happens in stages:

**offline install:**

* the same system image used to load the ISO live-environment Desktop will get copied over to target.
    
* packages only needed on the live session and install process getting removed from target.
    
* after install is finished, we detect hardware used and I decides to remove unneeded driver and virtual machine packages.
    
offline install uses the same squashfs image used for the Live-Session of the ISO to copy the system to your HD, then removing unneeded apps, and configure user and boot process, after calamares is partitioning the disk.

This method does not need an internet connection at all.



**online install**

* pacstrap installs base system
    
* user select DE and can opt out packages, and basic Desktop packages getting added too that creates a list of packages getting installed in second stage.
    
* after install is finished, we detect hardware used and I decides to remove unneeded driver and virtual machine packages.
Online method lets you choose your Desktop environment to install and have options to install printing support or Accessibility Tools, it is possible to remove also single packages from the list.

[install-scripts](https://github.com/endeavouros-team/calamares/tree/calamares/data/eos/scripts)

This method needs a working internet connection to proceed and will install the chosen DE „vanilla“ (no theming and configuration on the DE itself) as it would do on Archlinux itself. But with a minimal selection of packages to get a base Desktop to start making it your own.

The choosen DE (Desktop Environment) has deselectable groups for the EndeavourOS theming/fixes to be able to install it without our changes.

![selector](https://raw.githubusercontent.com/endeavouros-team/EndeavourOS-Development/main/images/eos-theme-deselect-kde-galileo.png)

DEs are only fixed to work properly per default mainly and we added minimal changes to icons and theming in cases:

[endeavouros-DE-fixes](https://github.com/endeavouros-team/endeavouros-DE-fixes)

## Calamares:
![squid](https://raw.githubusercontent.com/calamares/calamares/calamares/src/branding/default/squid.png)

[Calamares](https://calamares.io/)

We do use the our own fork of calamares sources for our install. Some modules are taking as they are and only configured to work for EndeavourOS install (Archlinux) others are created on our own like the pacstrap module used for the online install option. And some are modified to fit into what we need to setup for EndeavourOS. 

[EndeavourOS Calamares scripts and configuration](https://github.com/endeavouros-team/calamares/tree/calamares/data/eos)

Also, both online and offline install using the same calamares application.
We do use welcome app and different settings.conf files to schedule both install methods.

## Dependencies:

[Calamares Dependencies](https://github.com/endeavouros-team/calamares#readme)


