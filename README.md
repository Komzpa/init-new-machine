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
sudo eatmydata aptitude -y install axel
# development
sudo eatmydata aptitude -y install make graphviz pv postgresql-client pypy python-autopep8
sudo eatmydata aptitude -y install git
sudo eatmydata aptitude -y install docker-compose
# monitoring
sudo eatmydata aptitude -y install libdbd-pg-perl munin munin-node
sudo munin-node-configure --shell | sudo bash
sudo service munin-node restart
```
  
## GUI

```
proprietary: xmind viber slack google-earth-stable

chrome: https://www.google.com/chrome/
sudo snap install datagrip --classic

sudo eatmydata aptitude install git-cola mplayer krusader
```
