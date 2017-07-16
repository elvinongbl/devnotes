Table of Contents

- [Setup](#setup)
- [Start-up wireshark](#start-up-wireshark)
- [Add New Time Delta Column](#add-new-time-delta-column)
- [tshark (Console Version of Wireshark)](#tshark-console-version-of-wireshark)
  * [tshark and Lua Scripting](#tshark-and-lua-scripting)

# Setup

To install wireshark from standard Ubuntu build (tested with 16.04) and
set it up such that non-supervisor user can start wireshark, we need to
make sure wireshark group is added to a user's group.

```
sudo apt-get install wireshark
sudo usermod -a -G wireshark <user-name>
# Log-out and re-login to system again
# and check that wireshark is enlisted to a user's group
groups
```

# Start-up wireshark

To start wireshark, simply type below:-

```
wireshark &
```

<img src="images/wireshark/wireshark-start-up.png" width="500" height="500" />

# Add New Time Delta Column

1) Right click on column and choose column preferences:-
<img src="images/wireshark/wireshark-column-preferences.png" width="400" height="300" />

2) Add a new column by clicking on '+' button:-
<img src="images/wireshark/wireshark-add-column.png" width="500" height="500" />

3) Change the column 'name' and choose 'time-delta' for 'type', then click 'OK':-
<img src="images/wireshark/wireshark-column-type.png" width="500" height="450" />

4) You may also press and drag newly created column to the position you desired:-
<img src="images/wireshark/wireshark-time-delta.png" width="500" height="400" />

# tshark (Console Version of Wireshark)

tshark is the console version of Wireshark, a network protocol analyzer.
It captures network packets in pcap format, the same format used in tcpdump.

To install tshark on Ubuntu machine, type:-
```
sudo apt-get install tshark
```

Some examples of tshark common usages:-

- To capture a limited number of network packets
```
tshark -c [number of packets]
```

- To limit captures according to duration (in seconds)
```
tshark -a duration:X
```
<img src="images/wireshark/tshark-set-duration.png" width="816" height="120"/>

- To list network interfaces and use one for packet capturing
```
tshark -D
tshark -i <name of interface listed above>
```
<img src="images/wireshark/tshark-list-interfaces.png" width="506" height="205"/>

We may also specify multiple interfaces as shown below:
<img src="images/wireshark/tshark-set-2-interfaces.png" width="819" height="57"/>

Note: If there is no network interface selected, tshark selects the 1st non-loopback
interfaces.

- To put an interface as monitor mode

Note: the following steps do not work for network interface on virtualization.

When an interface enters monitor mode, it disassociates itself from the network
and enter into monitoring network packets. It enters stealth mode where no more
external network access is possible.

If we want all interfaces to be in monitor mode, place -I ahead of -i.
```
tshark -I -i <I/F-1> -i <I/F-2>
```
If we want to specify only one interface to enter monitor mode:
```
tshark -i <I/F-1> -I -i <I/F-2>
```

## tshark and Lua scripting
We can write lua script and registers
functions with tshark for (1) dissectors, (2) post-dissectors & (3) taps.

To ask tshark to execute Lua script, we use:-
```
tshark -X lua_script:<xyz.lua>
```

For example, running a hello world Lua script:-
<img src="images/wireshark/tshark-lua-hello.png" width="575" height="207"/>

For more notes on Lua scripting for Wireshark, please see [docs/tshark-lua](tshark-lua.md)
