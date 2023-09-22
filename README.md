![EndeavourOS Logo](https://raw.githubusercontent.com/endeavouros-team/artwork-images-logo/master/endeavouros-icon.png)

# EndeavourOS Installer

EndeavourOS provides a bootable Live-ISO that uses the Calamares installer framework to facilitate the installation of an Arch-based system.

## Key Features:

- **Arch-ISO Base**: Built on the same foundation as the Archlinux ISO.
- **Live XFCE4 Desktop Session**: A fully functional desktop environment that includes Firefox Browser, File Browser, Media Player, and various system tools.
- **Welcome App**: Launches the graphical [Calamares installer](https://calamares.io/), provides the latest release info, and offers insights about EndeavourOS.
- **Installation Options**:
  - **Offline Install**: Installs a default XFCE4 Desktop with EndeavourOS themes and configurations.
  - **Online Install**: Lets you choose your Desktop environment, fetches everything directly from the internet, and offers customization options like printing support and accessibility tools.

![Installer Screenshot](https://raw.githubusercontent.com/endeavouros-team/EndeavourOS-Development/main/images/2021-08-25_11-24.png)

## Community Editions

Discover community editions maintained and developed by community members:
- [EndeavourOS-Community-Editions Repository](https://github.com/EndeavourOS-Community-Editions)

## Building the ISO:

All essential resources to build the ISO are found here:
- [EndeavourOS-ISO Repository](https://github.com/endeavouros-team/EndeavourOS-ISO)

Key Components:
- [packages.x86_64](https://github.com/endeavouros-team/EndeavourOS-ISO/blob/main/packages.x86_64)
- [run_before_squashfs.sh](https://github.com/endeavouros-team/EndeavourOS-ISO/blob/main/run_before_squashfs.sh)
- [cleaner_script.sh](https://github.com/endeavouros-team/EndeavourOS-calamares/blob/main/calamares/scripts/cleaner_script.sh)
- [chrooted_cleaner_script.sh](https://github.com/endeavouros-team/EndeavourOS-calamares/blob/main/calamares/scripts/chrooted_cleaner_script.sh)

![Tools Screenshot](https://raw.githubusercontent.com/endeavouros-team/EndeavourOS-Development/main/images/2021-08-25_11-50.png)

## Online vs Offline Install:

**Offline Install**:
- System image from the ISO live-environment is copied to the target.
- Removal of packages only needed during the live session.
- Hardware detection post-install to remove unnecessary drivers and VM packages.

**Online Install**:
- Base system installation via pacstrap.
- Allows user-selected DE and optional package removals.
- Hardware detection post-install to remove unnecessary drivers and VM packages.

Packages for online install can be found here:
- [install-scripts](https://github.com/endeavouros-team/EndeavourOS-calamares/blob/main/calamares/scripts/)

![Installation Process Screenshot](https://raw.githubusercontent.com/endeavouros-team/EndeavourOS-Development/main/images/2021-08-25_11-28.png)

## DE Fixes

Other Desktop Environments are pre-configured for optimal performance:
- [endeavouros-DE-fixes Repository](https://github.com/endeavouros-team/endeavouros-DE-fixes)

## Calamares:

![Calamares Logo](https://raw.githubusercontent.com/calamares/calamares/calamares/src/branding/default/squid.png)

We utilize the latest Calamares sources for our installations. While many modules are used as-is, some are custom-made for EndeavourOS, such as the pacstrap module for online installations.

Discover more about our Calamares configuration and scripts:
- [EndeavourOS Calamares scripts and configuration](https://github.com/endeavouros-team/calamares/tree/calamares/data/eos)

Both online and offline installations use the same Calamares application, but with different configurations managed by the welcome app.

## Dependencies:

For a detailed list of dependencies:
- [Calamares Dependencies](https://github.com/endeavouros-team/calamares#readme)
