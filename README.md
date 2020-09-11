# arch-install-xps9300
## Arch install scripts for Dell XPS 9300

This script is most likely outdated and is only here for a reference. You should always check for the latest information on the [ArchWiki Installation Guide](https://wiki.archlinux.org/index.php/installation_guide).

This script is customized to my specific needs, but can be used as a basis for others scripts.  It is recommended to fork this and customize for your own needs. It is also highly recommended to study this script and understand what each command is doing and why.  A full understand of Arch will be very helpful. This script was created to help me quickly reinstall Arch while I experiment.

### Assumptions

That you have read and made all neccesary changes related to the machine from the [Dell XPS 13 (9300) ArchWiki](https://wiki.archlinux.org/index.php/Dell_XPS_13_(9300)).

This script assumes your will be using EFI and Grub and that your partitions are set up in a specific way.  The sizes do not matter, but the partition numbers do.  These could be modified easily by adjusting the script as needed, but the assumption below is the default.

/dev/nvme0n1p1 - EFI System
/dev/nvme0n1p2 - Linux swap
/dev/nvme0n1p3 - Linux filesystem

The rest will be handled by the script.

### Running the script

Download the latest live disk and prepare a USB drive as explained in 
- iwctl station wlan0 connect [ssid]
- pacman -Sy git
- git clone https://github.com/dkmcgowan/arch-install-xps9300
- zsh arch-xps9300.install [ssid] [passphrase] [root-password] [username] [password] [printer-ipaddress] 2>&1 | tee install.log


- Modify hostname as needed
- Update hosts with correct hostname and IP address

- add back reminna connections
- connect online accounts
- install 1password in firefox
- set vscode back up
