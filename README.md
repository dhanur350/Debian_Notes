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

## Install MongoDB in Debian Linux

- wget -qO - https://www.mongodb.org/static/pgp/server-5.0.asc | sudo apt-key add -
- echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/5.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-5.0.list
- sudo apt update
- sudo apt-get install -y mongodb-org
## Start mongodb
- sudo systemctl start mongod
- sudo systemctl enable mongod
- sudo systemctl status mongod

## Install MySQL
- sudo apt install snapd
- snap install gnome-3-38-2004
- snap install mysql-server mysql-workbench-community

# If this doesn't work then try this
# Download this config repo from mysql original website to add it in repo of linux
- sudo dpkg -i mysql-apt-config_0.8.22-1_all1.deb
- sudo apt update
- sudo apt install mysql-server

## Google Meet Screen Sharing problem Solution
- sudo nano /etc/gdm3/daemon.conf
- uncomment the line
- #WaylandEnable=false to be WaylandEnable=false and then reboot
- This'll solve all problems of Google Meet Screen issue

## Set Airplane mode disabled while lid is closed
# I'm facing wifi turn off issue when laptop lid is closed, then I tried this command
- sudo setkeycodes e058 245 e057 245
- It's working

## Install Tomcat-9 in Debian
- sudo apt install tomcat9 tomcat9-admin
- ss -ltn
- sudo sytemctl enable tomcat9
- sudo ufw allw from any to any port 8080 proto tcp
- If ufw doesn't work then run sudo apt install ufw
- `To check it's working simple type localhost:8080`
- `You'll see something like this "Tomcat9 is working successfully"`