# Debian_Notes
- To install debian, and it's superfast and amazing OS
## Modify and add these lines in /etc/apt/sources/list
- deb http://security.debian.org/debian-security bullseye-security main contrib
- deb-src http://security.debian.org/debian-security bullseye-security main contr>
- deb http://ftp.debian.org/debian bullseye main
- deb-src http://ftp.debian.org/debian bullseye main
- deb http://deb.debian.org/debian/ bullseye-updates main contrib
- deb-src http://deb.debian.org/debian/ bullseye-updates main contrib
## To fix WiFi in Debian 11 use these following commands
- wget -c http://ftp.us.debian.org/debian/pool/non-free/f/firmware-nonfree/firmware-iwlwifi_20210315-3_all.deb
- sudo dpkg -i firmware-iwlwifi_20210315-3_all.deb
- sudo modprobe -rv iwlwifi
- sudo modprobe -v iwlwifi
## To get G++ and GCC installed 
- sudo apt-get install build-essential