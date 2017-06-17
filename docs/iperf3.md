# Setup

## Server
iperf3 measures throughput between server and client. To ensure that measurement
is not due to CPU bandwidth limitation, it is advisable that server is running
on machine of higher computing power.

You may also setup such that a Linux VM is serving as server. In my current
setup, I allocate two network interfaces to my Linux VM as shown below:

1) 1st adapter is attached to bridged adapter of the Wi-Fi port.

<img src="images/iperf3/1st-adapter.png" width="400" height="200" />

2) 2nd adapter is attached to bridged adapter of the Ethernet port.

<img src="images/iperf3/2nd-adapter.png" width="400" height="200" />

## Client (DUT)

