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

## Installing Java in Debian 

Hello guys,  Download java 8, if you are using x64 OS Linux then download this file jdk-8u333-linux-x64.tar.gz 
then extract that file.... 
rename that folder... ( my folder name jdk-8)
move that folder here  /usr/lib/jvm/      ( java folder path )

*plz note :  my folder name jdk-8 , change your java folder name  /usr/lib/jvm/{here}/
loader.jar  is java8 testing file ( burp suite software )
then  switch your java version ... 
sudo update-alternatives --config java

then export path in bashrc file like this
export PATH="$PATH:/usr/lib/jvm/jdk-8/bin"

then create  java alternative version... type this commands..

sudo update-alternatives --install /usr/bin/java java /usr/lib/jvm/jdk-8/bin/java 1
sudo update-alternatives --install /usr/bin/javac javac /usr/lib/jvm/jdk-8/bin/javac 1
sudo update-alternatives --install /usr/bin/jar jar /usr/lib/jvm/jdk-8/bin/jar 1
sudo update-alternatives --config java

You'll see this written in the terminal
java version "1.8.0_333"
Java(TM) SE Runtime Environment (build 1.8.0_333-b02)
Java HotSpot(TM) 64-Bit Server VM (build 25.333-b02, mixed mode)

That means you successfully installed Java