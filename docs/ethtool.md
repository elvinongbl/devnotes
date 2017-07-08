# A) Overview

  - [Installation](#installation)
  - [Show Basics Network Device Information](#show-basics-network-device-information)

# 1) Installation

For Ubuntu system, simply run below command:

```
sudo apt-get install ethtool
```

For Yocto Project-built Linux OS, to pre-install ethtool on target OS, please
make sure:-

 - conf/local.conf    : IMAGE_INSTALL += "ethtool"

# 2) Show Basics Network Device Information

To show basic network device informations such as auto negotiation, link status,
speed, duplex mode & etc, we use

```
# Show device node available on your system.
ifconfig
# Select a device node for below command.
ethtool <devname>
```

<img src="images/ethtool/ethtool-eth0.png" width="680" height="414" />

# 3) Pause Frame

IEEE 802.3x defines a mechanism for temporarily stopping the transmission of
Ethernet data. To display flow control state of Ethernet port and setting them
independently, we use:-

```
# To show
ethtool -a <devname>
# To change flow control of device
ethtool -A <devname> [autoneg on|off] [rx on|off] [tx on|off]
```

<img src="images/ethtool/ethtool-get-set-pause.png" width="705" height="211" />
