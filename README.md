![alt text](https://raw.githubusercontent.com/endeavouros-team/artwork-images-logo/master/endeavouros-icon.png)
## EndeavourOS installer

EndeavourOS is mainly developing a bootable Live-ISO.
Using calamares installer framework to get an Archbased system installed.


**Based on Arch-ISO:**

we do use the same base as Archlinux itself is using for the ISO, but we implement a live Desktop session with XFCE 4 starting on Arch-ISO boot.

The XFCE4 live session is a fully working Desktop with all you need, Firefox Browser, Filebrowser, Mediaplayer, and extra many tools for system-tasks.

We do use our welcome-app to start the graphical installer [Calamares](https://calamares.io/) where you can read the latest release Info and get knowledge around EndeavourOS at all.

You can start gparted partition manager, and a selection of rescue tools, you can choose between offline install (Default XFCE4 Desktop themed and configured) or netinstall where you can choose the Desktop-Environment you want to install, what will perform an installation directly loading everything fresh from the internet.

In addition welcome has also a installer starter for community editions maintained and developed by community members:
[EndeavourOS-Community-Editions](https://github.com/EndeavourOS-Community-Editions)

![alt text](https://raw.githubusercontent.com/endeavouros-team/GitHub-page/main/images/2021-08-25_11-24.png)


**All that is needed to build the ISO is available here:**

[EndeavourOS-iso-next](https://github.com/endeavouros-team/EndeavourOS-iso-next)

Packages used for the squashfs-image and the Live-Session:

[run_before_squashfs.sh](https://github.com/endeavouros-team/EndeavourOS-iso-next/blob/master/packages.x86_64)

Changes we need to implement to the squashfs-image are made with this:

[run_before_squashfs.sh](https://github.com/endeavouros-team/EndeavourOS-iso-next/blob/master/run_before_squashfs.sh)


Our magic cleaner_scripts doing some magic we need to get all working as we want:

[cleaner_script.sh](https://github.com/endeavouros-team/install-scripts/blob/master/cleaner_script.sh)
[chrooted_cleaner_script.sh](https://github.com/endeavouros-team/install-scripts/blob/master/chrooted_cleaner_script.sh)

![alt text](https://raw.githubusercontent.com/endeavouros-team/GitHub-page/main/images/2021-08-25_11-50.png)

## Offline install:

offline install uses the same squashfs image used for the Live-Session of the ISO to copy the system to your HD, then removing unneeded apps, and configure user and boot process, after calamares is partitioning the disk.

This method does not need an internet connection at all.

## Netinstall:

Netinstall method let you choose your Desktop environment to install and have options to install printing support or Accessibility Tools, it is possible to remove also single packages from the list.

packages used for this are simply a list (written in YAML) you can find here:

[install-scripts](https://github.com/endeavouros-team/install-scripts)

This method needs a working internet connection to proceed and will install the chosen DE „vanilla“ (no theming and configuration on the DE itself) as it would do on Archlinux itself. But with a minimal selection of packages to get a base Desktop to start making it your own.

XFCE4 and i3 have unselectable groups for the EndeavourOS theming.

![alt text](https://raw.githubusercontent.com/endeavouros-team/GitHub-page/main/images/2021-08-25_11-28.png)

## Calamares:
[Calamares](https://calamares.io/)

We do use the latest calamares sources for our install. Most modules are taking as they are and only configured to work for EnOS install (Archlinux) others are created on our own like the pacstrap module used for netinstall.

[EndeavourOS Calamares Modules](https://github.com/endeavouros-team/Calamares_current)

Also, both online and offline install using the same calamares.
We do use welcome app and different settings.conf files to schedule the both installl methoids and handling Community Editions.

## Dependencies:

[Calamares Dependencies](https://github.com/calamares/calamares/blob/master/README.md)


