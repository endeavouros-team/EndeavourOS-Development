![icon](https://raw.githubusercontent.com/endeavouros-team/artwork-images-logo/b53c4b90276e77d530785cb60d33c6bc3cc02f45/icons/endeavour-logo-sans-logotype.svg)

## [EndeavourOS](https://endeavouros.com) installer

EndeavourOS is mainly developing a bootable Live-ISO using calamares installer framework to get an
Archbased Desktop installed.

## Contributing to Development

We welcome any contribution, be it only correcting a typo, providing fixes for used code, making
suggestions, or reporting issues.

Start contributing by opening a pull request. If you start contributing over a longer period, and
you want to join the EndeavourOS team, then we can discuss changing your permissions.

- **Translations**
    - For Calamares Modules and Information shown in install process
        - [Calamares Translations](https://github.com/endeavouros-team/calamares/blob/calamares/data/eos/calamares-translations.txt)
- For EndeavourOS Applications (welcome per example)
    - [EndeavourOS Apps translations](https://github.com/endeavouros-team/PKGBUILDS/tree/master/eos-translations)
- **Installer (Calamares)**
    -  Start having a look at the code and information on the Calamares Repository (we use a forked
       version):
        - [Calamares Installer](https://github.com/endeavouros-team/calamares)
- **ISO build Framework**
    - A hugely modified version of the original Archiso
        - [EndeavourOS-ISO](https://github.com/endeavouros-team/EndeavourOS-ISO)
- **EndeavourOS Applications**
    - Have have a look at the repositories
        - [EndeavourOS Code Repositories](https://github.com/orgs/endeavouros-team/repositories)
- **EndeavourOS ISO Features**
    - We use the same ISO base image as Archlinux, but we implement a live Desktop session with KDE
      starting on Arch-ISO boot.
    - The KDE live session is a fully working Desktop with all you need: Firefox Browser, Filebrowser,
      Mediaplayer, and many extra tools for system tasks.
    - We use our welcome-app to start the graphical installer, [Calamares](https://calamares.io/),
      where you can read the latest release info.
    - You can start the gparted partition manager and a selection of rescue tools. You can choose
      between offline install (only the same as the LiveSession: KDE Desktop), or netinstall, where
      you can choose the Desktop Environment and install everything directly from the Internet.

![calamares installer kde galileo](https://raw.githubusercontent.com/endeavouros-team/EndeavourOS-Development/main/images/livesession-kde-galileo.png)

## Building the ISO

- [EndeavourOS-ISO](https://github.com/endeavouros-team/EndeavourOS-ISO)
- Packages used for the squashfs-image and the Live-Session
  - [packages.x86_64](https://github.com/endeavouros-team/EndeavourOS-ISO/blob/main/packages.x86_64)
- Changes we need to implement to the squashfs-image are made with this
  - [run_before_squashfs.sh](https://github.com/endeavouros-team/EndeavourOS-ISO/blob/main/run_before_squashfs.sh)
- Our magic cleaner_scripts doing some magic we need to get all working as we want
  - [cleaner_script.sh](https://github.com/endeavouros-team/calamares/blob/calamares/data/eos/scripts/cleaner_script.sh)
  - [chrooted_cleaner_script.sh](https://github.com/endeavouros-team/calamares/blob/calamares/data/eos/scripts/chrooted_cleaner_script.sh)

## Installing EndeavourOS

![calamares installer](https://raw.githubusercontent.com/endeavouros-team/EndeavourOS-Development/main/images/online-offline-welcome-kde-galileo.png)

The EndeavourOS installer setup differs in one major way from most other distros using Calamares.
That is, the online installer installs the system from scratch since it is not using the ISO image.

The installation occurs in stages, and there are several different installation methods:

1. **Offline install**
   - The same system image used to load the ISO live-environment Desktop will get copied over to the
     target.
   - Packages only needed on the live session and install process get removed from the target.
   - After the install is finished, it detects the hardware and then  decides to remove unneeded
     driver and virtual machine packages.
   - After Calamares partitions the disk, the offline install uses the same squashfs image used for
     the Live-Session of the ISO to copy the system to your hard drive, remove unneeded apps, and
     configure the user and boot process.
   - This method does not need an internet connection at all.
2. **Online install**
   - Pacstrap installs base system.
   - User select DE (Desktop Environment), can opt out packages, and basic Desktop packages are added
     to a list that get installed in the second stage.
   - After the install is finished, hardware is detected, and unneeded driver and virtual machine
     packages are removed.
   - The online method lets you choose your Desktop environment to install and havs options to
     install printing support or Accessibility Tools. It is also possible to remove single packages
     from the list.
3. [**install-scripts**](https://github.com/endeavouros-team/calamares/tree/calamares/data/eos/scripts)
   - This method needs a working internet connection to proceed.
   - It will install the chosen DE with no theming or configuration, just like it would do on
     Archlinux. It also installs a minimal selection of packages to get a base Desktop that you can
     start customizing to fit your needs.
   - The choosen DE has deselectable groups for the EndeavourOS theming/fixes to be able to install
     it without our changes.

![selector](https://raw.githubusercontent.com/endeavouros-team/EndeavourOS-Development/main/images/eos-theme-deselect-kde-galileo.png)

By default, [DEs are only fixed](https://github.com/endeavouros-team/endeavouros-DE-fixes) to work
properly.  In some cases we made minimal changes to icons and theming.

### Installer options

1. You can select between systemd-boot (default), Grub, or to not install any bootloader in case you
   are using your own.
2. Automatic Partition with presets, or manual partioning where it is up to you to select how to
   setup and mount partitions.  In this case you have to set **ESP mount** to `/efi` if you select
   **systemd-boot** and `/boot/efi` in case you are using **Grub** as the bootloader.

![bootloader](https://github.com/endeavouros-team/EndeavourOS-Development/assets/16797647/120fc78b-4dfb-44a9-8fba-6ca064b87f57)

## Calamares

<img src="https://raw.githubusercontent.com/calamares/calamares/calamares/src/branding/default/squid.png" width="150" height="150">

We use our own fork of [Calamares](https://github.com/endeavouros-team/calamares). Some modules
are taken as they are and only configured to work for EndeavourOS.  Others are created on our
own, like the pacstrap module used for the online install option.  A few modules are modified to fit
into what we need to setup EndeavourOS.  You can find the scripts and configurations in our
[Calamares GitHub repository](https://github.com/endeavouros-team/calamares/tree/calamares/data/eos).

Both online and offline install use the same Calamares application.  We use the welcome app and
different settings.conf files to distinguish between the two installation methods.

### Calamares dependencies

You can find the [Calamares Dependencies](https://github.com/endeavouros-team/calamares#readme)
on GitHub.
