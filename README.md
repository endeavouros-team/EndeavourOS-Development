![alt text](https://raw.githubusercontent.com/endeavouros-team/artwork-images-logo/master/endeavouros-icon.png)

## EndeavourOS installer

EndeavourOS is mainly developing a bootable Live-ISO.
Using calamares installer framework to get an Arch-based system installed.


**EndeavourOS ISO Features:**

We use the same base as Archl Linux itself is using for the ISO, but we implement a live desktop session with XFCE starting on Arch-ISO boot.

The XFCE live session is a fully working Desktop with all you need, Firefox Browser, Filebrowser, Mediaplayer, and extra many tools for system tasks.

We use our welcome-app to start the graphical installer. You can read the latest release Info and get knowledge around EndeavourOS at [Calamares](https://calamares.io/).

You can start gparted partition manager and a selection of rescue tools, you can choose between the offline installation (which is the same as the live-session: EndeavourOS-themed XFCE Desktop) or the netinstall, where you can choose the Desktop-Environment you want to install, which will perform an installation directly loading everything from the internet. 
![calamares installer kde galileo](https://raw.githubusercontent.com/endeavouros-team/EndeavourOS-Development/main/images/livesession-kde-galileo.png)

**Everything needed to build the ISO is available here:**

[EndeavourOS-ISO](https://github.com/endeavouros-team/EndeavourOS-ISO)

Packages used for the squashfs-image and the live-session:

[packages.x86_64](https://github.com/endeavouros-team/EndeavourOS-ISO/blob/main/packages.x86_64)

Changes we need to implement to the squashfs-image are made with this:

[run_before_squashfs.sh](https://github.com/endeavouros-team/EndeavourOS-ISO/blob/main/run_before_squashfs.sh)


Our magic cleaner_scripts doing some magic to get all working as intended:

[cleaner_script.sh](https://github.com/endeavouros-team/calamares/blob/calamares/data/eos/scripts/cleaner_script.sh)

[chrooted_cleaner_script.sh](https://github.com/endeavouros-team/calamares/blob/calamares/data/eos/scripts/chrooted_cleaner_script.sh)

![calamares installer](https://raw.githubusercontent.com/endeavouros-team/EndeavourOS-Development/main/images/online-offline-welcome-kde-galileo.png)

The EndeavourOS installer setup differs in one major way too most other Distributions using Calamares.

Install happens in stages:

**Offline installation:**

    a. the same system image used to load the ISO live-environment Desktop will get copied over to target.
    
    b. packages only needed on the live session and install process getting removed from target.
    
    c. after install is finished, we detect hardware used and I decides to remove unneeded driver and virtual machine packages.
    
The offline installation uses the same squashfs image used for the Live-Session of the ISO to copy the system to your disk, then removing unneeded apps, and configure user and boot process, after calamares is partitioning the disk.

This method does not need an internet connection at all.



**Online installation**

    a. Pacstrap installs base system
    
    b. User selects DE and can opt out packages. Some basic desktop packages getting added too. That creates a list of packages getting installed in second stage.
    
    c. After the installation is finished, we detect hardware used and we decided to remove unneeded drivers and virtual machine packages.
The online method lets you choose your Desktop environment to install and have options to install printing support or Accessibility Tools, it is possible to remove also single packages from the list. The Online method is not using the ISO image at all and installs the system fresh from scratch.

[install-scripts](https://github.com/endeavouros-team/calamares/tree/calamares/data/eos/scripts)

This method needs a working internet connection to proceed and will install the chosen DE „vanilla“ (no theming and configuration on the DE itself) as it would be on Arch Linux itself, but with a minimal selection of packages in order to get a base desktop to start making it your own.

The choosen DE (Desktop Environment) has deselectable groups for the EndeavourOS theming/fixes to be able to install it without our changes.

![selector](https://raw.githubusercontent.com/endeavouros-team/EndeavourOS-Development/main/images/eos-theme-deselect-kde-galileo.png)

DEs are only fixed to work properly per default. We added minimal changes to icons and theming in cases:

[endeavouros-DE-fixes](https://github.com/endeavouros-team/endeavouros-DE-fixes)

## Calamares:
![squid](https://raw.githubusercontent.com/calamares/calamares/calamares/src/branding/default/squid.png)

[Calamares](https://calamares.io/)

We do use our own fork of calamares sources for our installation. Some modules are taken as they are and only configured to work for the EndeavourOS installation. Others are created on our own, like the pacstrap module used for the online installation option. Some are modified to fit into what we need to setup for EndeavourOS. 

[EndeavourOS Calamares scripts and configuration](https://github.com/endeavouros-team/calamares/tree/calamares/data/eos)

Also, both online and offline installation use the same calamares application.
We do use our welcome-app and a different settings.conf files to schedule both installation methods.

## Dependencies:

[Calamares Dependencies](https://github.com/endeavouros-team/calamares#readme)


