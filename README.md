# Arch install scripts for Dell XPS 9300

This script is most likely outdated and is only here for a reference. You should always check for the latest information on the [ArchWiki Installation Guide](https://wiki.archlinux.org/index.php/installation_guide). Things change a lot and releases happen all the time, the ArchWiki will keep all that information current.

This script is customized to my specific needs, but can be used as a basis for other installation scripts.  It is recommended to fork this and customize for your own needs. It is also highly recommended to study this script and understand what each command is doing and why.  A full understand of your system, what it's running, and how it was set up will be very helpful. This script was created to help me quickly reinstall Arch while I experiment with more dangerous and experimental changes.

This script installs all essential base packages, terminal tools, Xorg, display manager, desktop environment, and a handful of applications I find essential.

This script comes with 2 options for the Display Manager and the Desktop Environment.  You can choose LightDM/Cinnamon or GDM/Gnome. These are the only two current options because they both support and work well with the UHD screen on the XPS 9300.

All features of the XPS 9300 are set up and functional including hibernation, fingerprint reader, correct display driver, TLP is set up to help conserve battery, and throttled for throttling issues.

Howdy for IR camera login is not currently set up. It requires 5 additional AUR packages, some that require certain python 2 libraries, and the overall functionality does not integrate as well as password and fingerprint. It does work if interested, follow instructions [Howdy](https://wiki.archlinux.org/index.php/Howdy)

## Assumptions

That you have read and made all neccesary changes related to the machine from the [Dell XPS 13 (9300) ArchWiki](https://wiki.archlinux.org/index.php/Dell_XPS_13_(9300)).

This script assumes your will be using EFI and Grub and that your partitions are set up in a specific way.  The sizes do not matter, but the partition numbers do.  These could be modified easily by adjusting the script as needed, but the assumption below is the default.

* /dev/nvme0n1p1 - EFI System
* /dev/nvme0n1p2 - Linux swap
* /dev/nvme0n1p3 - Linux filesystem

The rest will be handled by the script.

More information on partitioning can be found at [Partition the disks](https://wiki.archlinux.org/index.php/installation_guide#Partition_the_disks)

## Running the script

Download the latest live disk and prepare a USB drive as explained in [Prepare an installation medium](https://wiki.archlinux.org/index.php/installation_guide#Prepare_an_installation_medium).

Next you will connect to the internet, install Git, clone the repository locally, and execute the script to complete the installation. It will send the output to both console and the install.log file. If you want to review the log file for errors, you should hit "n" when asked to Reboot because the install.log file will be lost once you reboot.

* iwctl station wlan0 connect [ssid]
* pacman -Sy git
* git clone https://github.com/dkmcgowan/arch-install-xps9300
* zsh arch-xps9300.install [ssid] [passphrase] [root-password] [username] [password] 2>&1 | tee install.log

## Installation

The installation will ask a few questions. First you will select your display manager and desktop environment then you will be asked to enter the machine hostname and IP address. If you do not have a static IP address just leave the default 127.0.1.1. You can also enter the IP address of an HP printer and it will also be set up during installation, if you do not have an HP printer leave this as the default na.  The HP is the only printer this asks to set up because that is the printer that I use.

## Remaining set up steps after installation

These are notes for things on my default installation that I did not include yet in this script.

* Set up reminna remote desktop connections
* Connect online accounts (gdrive)
* Install 1Password X in Firefox and Chromium
* Set up vscode SSH connections and settings (use sshfs, remote development extension doesn't work on code oss)
* Configure name/email with git
* Authorize and set up dropbox (selective sync)
* Set Firefox default zoom to 110%
* Set Weather City
* Enable Search in Activities for Weather
* Make default browser/web Firefox
* Set up VPN
* Enable location services in gnome settings
* Install slack and zoom packages, move them to first page of apps in activities / app view
* Set system sounds volume in gnome
* Gnome, set hide all normal windows from disabled to Super+D
* Add MOZ_USE_XINPUT2 DEFAULT=1 to /etc/security/pam_env.conf and then logout or reboot your system
* Update terminal pallete to GNOME with highlights for bold checked
* comment out homed reference in system_auth pam.d
