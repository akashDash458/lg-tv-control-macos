# LG TV Control for macOS

Forked from [cmer/lg-tv-control-macos](https://github.com/cmer/lg-tv-control-macos)

Original Features:
- Automatically wake/sleep and change the input of your LG TV when used as a monitor on macOS.
- Audio Control


Added features:
- Detect new display being connected and turn the new display on
- Apply input settings to the new display (set mode to PC, change connection name)




This script uses Hammerspoon to detect system events such as power off, sleep, and wake.

## Pre-installation Requirements

- [Homebrew](https://brew.sh/)

### Installation

Use the installation script for a simple and convenient installation process.

Before proceeding, make sure you have [Homebrew](https://brew.sh) installed. All the other dependencies will be installed automatically:

- [Mise](https://mise.jdx.dev/)
- Python 3.8.18
- [Hammerspoon](https://www.hammerspoon.org/)
- [LGWebOSRemote](https://github.com/klattimer/LGWebOSRemote).
- [bscpylgtvcommand](https://github.com/chros73/bscpylgtv)

Run the following commands in Terminal:

```bash
cd /tmp
git clone https://github.com/cmer/lg-tv-control-macos.git
cd lg-tv-control-macos
./install.sh
```


#### Removing old versions of LGWebOSRemote

If you had previously installed LGWebOSRemote with PIP,
you can remove the old version by running:

```
rm -fr ~/opt/lgtv
```

### Configuring LGWebOSRemote

By now, you should be able to run

```sh
~/bin/lgtv scan ssl
```

and see some info about your TV. Grab your TV's IP address from the output. Then:

```sh
~/bin/lgtv auth <ip_address_here> MyTV --ssl
```

and follow the instructions on your TV.

Now, try the following:

```sh
~/bin/lgtv --name MyTV --ssl swInfo
~/bin/lgtv --name MyTV --ssl screenOff
```
If everything is working as expected, your screen should turn off.

To turn it back on, try: 
```sh
~/bin/lgtv --name MyTV --ssl screenOn
```

### Changes needed to get the script working:
Following variables need to be changed in `~/.hammerspoon/init_lgtv.lua` as per the user's setup:
- `tv_input` : HDMI 1/2/3/4, depending on the connection.
- `tv_ip`: IP address of the TV. Can be found by running `~/bin/lgtv scan ssl`. (Might need to be changed if TV's network changes)
- `connection_name`: (optional) Preferred connection name, like `My Mac Book`


