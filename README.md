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

## Now there is a new bug whenever you feel installing Debian and miss minimize and maximize buttons on top left panel then write this command in terminal
- `gsettings set org.gnome.desktop.wm.preferences button-layout ":minimize,maximize,close"`

## Install .NET Core in Debian
- wget https://packages.microsoft.com/config/debian/11/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
rm packages-microsoft-prod.deb

- sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y dotnet-sdk-5.0
- sudo apt-get install -y dotnet-runtime-5.0

- sudo apt-get update; \ sudo apt-get install -y apt-transport-https && \ sudo apt-get update && \ sudo apt-get install -y aspnetcore-runtime-5.0

## Install Microsoft SQL server in Linux Debain
- wget -qO- https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
## This may seems to be weird to add Ubuntu Repo in debian Termainal Surces.list but this will be the only way to install MSSQL 
- sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/20.04/mssql-server-2019.list)"
# After that install MSSQL Server and Tools
- sudo apt-get update
- sudo apt-get install -y mssql-server
- sudo apt-get install mssql-tools
## Config MSSQL
- sudo /opt/mssql/bin/mssql-conf setup
- sudo ls /opt/mssql-tools/bin/sqlcmd*
- sudo ln -sfn /opt/mssql-tools/bin/sqlcmd /usr/bin/sqlcmd

## Connect Locally on MSSQL
- `sqlcmd -S localhost -U SA -P '<YourPassword>'`