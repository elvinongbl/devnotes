# A) Setup

## 1) Server

iperf3 measures throughput between server and client. To ensure that measurement
is not poor due to computing bottle-neck in server, it is advisable that server
is running on machine of higher computing power.

To install iperf3 on Ubuntu machine
```
sudo apt-get install iperf3
```

For Yocto Project-built Linux OS, to pre-install iperf3 on target OS, please
make sure:-

 - conf/bblayers.conf : include path to meta-openembedded/meta-oe
 - conf/local.conf    : IMAGE_INSTALL += "iperf3"

### 1.1(a) Linux VM with dual network adapters

You may also setup such that a Linux VM is serving as server. In my current
setup, I allocate two network interfaces to my Linux VM as shown below:

1) 1st adapter is attached to bridged adapter of the Wi-Fi port.

<img src="images/iperf3/1st-adapter.png" width="400" height="200" />

This adapter shall be used for general access to Internet.

2) 2nd adapter is attached to bridged adapter of the Ethernet port.

<img src="images/iperf3/2nd-adapter.png" width="400" height="200" />

This adapter shall be used to connect to DUT for iperf measurement.

Note:

IP addresses for server and client are statically assigned below:-

iperf3 server :- 172.169.0.1

iperf3 client :- 172.169.0.2

### 1.1(b) Setting IP address for the 2 adapters at Linux VM

Assuming 1st adapter is enp0s3 and 2nd is enp0s8, we configure
/etc/network/interfaces as:-
```
auto enp0s8
iface enp0s8 inet static
    address 172.169.0.1
    netmask 255.255.255.0
    gateway 172.169.0.2

auto enp0s3
iface enp0s3 inet dhcp
    netmask 255.255.255.0
    gateway 192.168.1.1
    dns-nameservers 192.168.1.1 8.8.8.8
    dns-domain acme.com
    dns-search acme.com
```

Fire up both network adapters at server end:
```
sudo ifup enp0s3
sudo ifup enp0s8
```

Check that IP routing table is properly setup and you still can ping
a server on Internet:
```
route
ping www.google.com
```

## 2) Client (DUT)

Assuming Ethernet network adapter for device under test (DUT) is eth0,
/etc/network/interfaces shall be configured as:-
```
auto eth0
iface eth0 inet static
    address 172.169.0.2
    netmask 255.255.255.0
    gateway 172.169.0.1
```

Start network adapter at client end (DUT):
```
sudo ifup eth0
```

# B) Testing

## iperf3 client is sending

Server-side:
```
iperf3 -s
```

Client-side:
```
iperf3 -c <server IP address>
```

Screen-shots:-

Client-side:

<img src="images/iperf3/iperf3-client-1.png" width="600" height="300" />

Server-side:

<img src="images/iperf3/iperf3-server-1.png" width="600" height="300" />

## iperf3 server is sending

Server-side:
```
iperf3 -s
```

Client-side:
```
iperf3 -c <server IP address> -R
```

Screen-shots:-

Client-side:

<img src="images/iperf3/iperf3-client-2.png" width="600" height="300" />

Server-side:

<img src="images/iperf3/iperf3-server-2.png" width="600" height="300" />

## iperf3 server and client are sending to each other

Server-side:
```
iperf3 -s
```

Client-side:
```
iperf3 -c <server IP address> -d
```
