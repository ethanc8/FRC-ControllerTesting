# Setting up pyspacemouse

## Debian/Ubuntu

First, uninstall `spacenavd` and reboot:
```bash
sudo apt remove libspnav-dev libspnav0 spacenavd
sudo reboot now
```

```bash
conda env create -f ../environment.yml
conda activate FRC-ControllerTesting
sudo apt-get install libhidapi-dev
echo 'KERNEL=="hidraw*", SUBSYSTEM=="hidraw", MODE="0664", GROUP="plugdev"' | sudo tee /etc/udev/rules.d/99-hidraw-permissions.rules
sudo usermod -aG plugdev $USER
newgrp plugdev
```
Note: `newgrp` will log into a new session.
```bash
conda activate FRC-ControllerTesting
pip3 install pyspacemouse
```

### Installing `hidapitester` (optional)

```bash
wget https://github.com/todbot/hidapitester/releases/download/v0.5/hidapitester-linux-x86_64.zip
unzip hidapitester-linux-x86_64.zip
cp hidapitester ~/.local/bin
```

## Windows