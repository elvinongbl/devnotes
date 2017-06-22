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

# Add a new column to show time delta

1) Right click on column and choose column preferences:-
<img src="images/wireshark/wireshark-column-preferences.png" width="400" height="300" />

2) Add a new column by clicking on '+' button:-
<img src="images/wireshark/wireshark-add-column.png" width="500" height="500" />

3) Change the column 'name' and choose 'time-delta' for 'type', then click 'OK':-
<img src="images/wireshark/wireshark-column-type.png" width="500" height="450" />

4) You may also press and hold newly created column to the position you desired:-
<img src="images/wireshark/wireshark-time-delta.png" width="500" height="400" />
