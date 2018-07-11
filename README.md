# init-new-machine
A repo with stuff I run on each new Ubuntu machine that comes along my way

## console

```
sudo apt-get update
sudo apt-get -y upgrade
sudo apt-get -y install eatmydata aptitude
# system management
sudo eatmydata aptitude -y install htop mc vim iotop hdparm smartmontools iperf nmap unattended-upgrades openntpd
# remote administration
sudo eatmydata aptitude -y install screen apg
# fast download manager
sudo eatmydata aptitude -y install axel curl wget
# development
sudo eatmydata aptitude -y install make graphviz pv postgresql-client pypy python-autopep8
sudo eatmydata aptitude -y install git
sudo eatmydata aptitude -y install docker-compose
# monitoring
sudo eatmydata aptitude -y install libdbd-pg-perl munin munin-node uptimed
sudo munin-node-configure --shell | sudo bash
sudo service munin-node restart

sudo apt install exfat-fuse exfat-utils

```
  
## GUI

```
proprietary: xmind viber slack google-earth-stable

chrome: https://www.google.com/chrome/
sudo snap install datagrip --classic
sudo snap install telegram-desktop 

sudo eatmydata aptitude install git-cola mplayer krusader
```

## Copy data

```
connect machines with gbit ethernet
echo Cipher arcfour >> .ssh/config
ssh kom@old-machine -c 'tar -c /home/kom' | pv | tar xv .
```
