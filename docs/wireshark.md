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
