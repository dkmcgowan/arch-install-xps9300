# arch-install-xps9300
Arch install scripts for Dell XPS 9300

- iwctl station wlan0 connect [ssid]
- pacman -Sy git
- git clone https://github.com/dkmcgowan/arch-install-xps9300
- zsh arch-xps9300.install [ssid] [passphrase] [root-password] [username] [password] [printer-ipaddress] 2>&1 | tee install.log

- Assumes partitions correct, describe fdisk and hard drive set up
- Modify hostname as needed
- Update hosts with correct hostname and IP address

- add back reminna connections
- connect online accounts
- install 1password in firefox
- set vscode back up
