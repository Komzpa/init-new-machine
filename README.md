# init-new-machine

Setup notes and bootstrap commands I run on new Ubuntu machines.

## CLI bootstrap

```bash
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
sudo eatmydata aptitude -y install make graphviz pv postgresql-client pypy python-autopep8 pspg
sudo eatmydata aptitude -y install git
sudo eatmydata aptitude -y install docker-compose
# node + npm (for AI CLIs)
sudo eatmydata aptitude -y install nodejs npm
# AI CLIs
sudo npm install -g @openai/codex @anthropic-ai/claude-code @google/gemini-cli npm
# monitoring
sudo eatmydata aptitude -y install libdbd-pg-perl munin munin-node uptimed
sudo munin-node-configure --shell | sudo bash
sudo service munin-node restart

sudo apt install exfat-fuse exfat-utils

```

## GUI

```bash
proprietary: xmind viber slack google-earth-stable

chrome: https://www.google.com/chrome/
sudo snap install datagrip --classic
sudo snap install telegram-desktop

sudo eatmydata aptitude install git-cola mplayer krusader
```

## Copy data from old machine

```bash
connect machines with gbit ethernet
mkdir -p ~/.ssh
echo Cipher arcfour >> ~/.ssh/config
ssh kom@old-machine -c 'tar -c /home/kom' | pv | tar xv .
```

## System tuning baseline (`sysctl` + kernel module)

Reference values with comments:

```conf
# Cap dirty page writeback threshold (~512 MiB). Helps avoid huge flush bursts.
vm.dirty_bytes=536870912

# Start background writeback at the same threshold.
# (Usually this is lower than vm.dirty_bytes; keep equal only if intentional.)
vm.dirty_background_bytes=536870912

# Favor swapping out anonymous pages more aggressively.
vm.swappiness=100

# Keep TCP from resetting congestion window after idle periods.
net.ipv4.tcp_slow_start_after_idle=0

# Optional core dump routing (disabled by default here):
#kernel.core_pattern=/mnt/storage/core/core.%e.%p.%h.%t
#fs.suid_dumpable=2

# Include PID in core dump file names.
kernel.core_uses_pid=1

# Allow limited TIME-WAIT socket reuse for new outgoing connections.
net.ipv4.tcp_tw_reuse=1

# Increase file watch capacity (useful for dev tools and sync daemons).
fs.inotify.max_user_watches=524288
```

Apply sysctl changes after editing:

```bash
sudo sysctl -p /etc/sysctl.conf
```

### Zoom flicker (UVC `nodrop`)

If Zoom flickers with a UVC webcam, set `uvcvideo nodrop=0`:

```bash
echo "options uvcvideo nodrop=0" | sudo tee /etc/modprobe.d/uvcvideo.conf
```
