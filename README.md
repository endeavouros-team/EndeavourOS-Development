![alt text](https://raw.githubusercontent.com/endeavouros-team/artwork-images-logo/master/endeavouros-icon.png)
## EndeavourOS installer

EndeavourOS is mainly developing a bootable Live-ISO.
Using calamares installer framework to get an Archbased system installed.


**Based on Arch-ISO:**

we do use the same base as Archlinux itself is using for the ISO, but we implement a live Desktop session with XFCE 4 starting on Arch-ISO boot.

The XFCE4 live session is a fully working Desktop with all you need, Firefox Browser, Filebrowser, Mediaplayer, and extra many tools for system tasks.

We do use our welcome-app to start the graphical installer [Calamares](https://calamares.io/) where you can read the latest release Info and get knowledge around EndeavourOS at all.

You can start gparted partition manager, and a selection of rescue tools, you can choose between offline install (Default XFCE4 Desktop themed and configured) or netinstall where you can choose the Desktop-Environment you want to install, what will perform an installation directly loading everything fresh from the internet.

In addition, welcome has also an installer starter for community editions maintained and developed by community members:
[EndeavourOS-Community-Editions](https://github.com/EndeavourOS-Community-Editions)

![alt text](https://raw.githubusercontent.com/endeavouros-team/EndeavourOS-Development/main/images/2021-08-25_11-24.png)


**All that is needed to build the ISO is available here:**

[EndeavourOS-ISO](https://github.com/endeavouros-team/EndeavourOS-ISO)

Packages used for the squashfs-image and the Live-Session:

[packages.x86_64](https://github.com/endeavouros-team/EndeavourOS-ISO/blob/main/packages.x86_64)

Changes we need to implement to the squashfs-image are made with this:

[run_before_squashfs.sh](https://github.com/endeavouros-team/EndeavourOS-ISO/blob/main/run_before_squashfs.sh)


Our magic cleaner_scripts doing some magic we need to get all working as we want:

[cleaner_script.sh](https://github.com/endeavouros-team/EndeavourOS-calamares/blob/main/calamares/scripts/cleaner_script.sh)
[chrooted_cleaner_script.sh](https://github.com/endeavouros-team/EndeavourOS-calamares/blob/main/calamares/scripts/chrooted_cleaner_script.sh)

![alt text](https://raw.githubusercontent.com/endeavouros-team/EndeavourOS-Development/main/images/2021-08-25_11-50.png)

The EndeavourOS installer setup differs in one Major way too most other Distros using Calamares and this is the online installer setup.
As it is not using the ISO image at all and installs the system fresh from scratch.

Install happens in stages:

**offline install:**

    a. the same system image used to load the ISO live-environment Desktop will get copied over to target.
    
    b. packages only needed on the live session and install process getting removed from target.
    
    c. after install is finished, we detect hardware used and I decides to remove unneeded driver and virtual machine packages.
    
offline install uses the same squashfs image used for the Live-Session of the ISO to copy the system to your HD, then removing unneeded apps, and configure user and boot process, after calamares is partitioning the disk.

This method does not need an internet connection at all.



**online install**

    a. pacstrap installs base system
    
    b. user select DE and can opt out packages, and basic Desktop packages getting added too that creates a list of packages getting installed in second stage.
    
    c. after install is finished, we detect hardware used and I decides to remove unneeded driver and virtual machine packages.
Online method lets you choose your Desktop environment to install and have options to install printing support or Accessibility Tools, it is possible to remove also single packages from the list.

packages used for this are simply a list (written in YAML) you can find here:

[install-scripts](https://github.com/endeavouros-team/EndeavourOS-calamares/blob/main/calamares/scripts/)

This method needs a working internet connection to proceed and will install the chosen DE „vanilla“ (no theming and configuration on the DE itself) as it would do on Archlinux itself. But with a minimal selection of packages to get a base Desktop to start making it your own.

XFCE4 has de-selectable groups for the EndeavourOS theming to be able to install it without our theming.

![alt text](https://raw.githubusercontent.com/endeavouros-team/EndeavourOS-Development/main/images/2021-08-25_11-28.png)

## Calamares:
![squid](https://raw.githubusercontent.com/calamares/calamares/calamares/src/branding/default/squid.png)

[Calamares](https://calamares.io/)

We do use the latest calamares sources for our install. Most modules are taking as they are and only configured to work for EndeavourOS install (Archlinux) others are created on our own like the pacstrap module used for the online install option.

[EndeavourOS Calamares scripts and configuration](https://github.com/endeavouros-team/EndeavourOS-calamares)

Also, both online and offline install using the same calamares application.
We do use welcome app and different settings.conf files to schedule both install methods and handling Community Editions.

## Dependencies:

[Calamares Dependencies](https://github.com/calamares/calamares/blob/master/README.md)


