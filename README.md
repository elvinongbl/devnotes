# Overview
This is my quick personal notes that I have gathered all these years when
I am dealing with Linux-based OS and system.

# Table of Content

[Editing in Markdown](#editing-in-markdown)

[Networking](#networking)
- [Setting-up /etc/network/interfaces](#setting-up-etcnetworkinterfaces)
- [Using ethtool](#using-ethtool)

[Git and GitHub Setup](#git-and-github-setup)
- [General Overview and Setup for git](#general-overview-and-setup-for-git)
- [Setting-up SSH Access](#setting-up-ssh-access)
- [Setting-up Github account](#setting-up-github-account)
- [Setting-up git-pw](#setting-up-git-pw)

[Performance Gathering](#performance-gathering)
- [For Processor](#for-processor)
- [For I/O Access](#for-i/o-acess)
- [For Networking](#for-networking)
  * [iperf3](#iperf3)
  * [wireshark](#wireshark)
  * [Lua scripting with tshark](#lua-scripting-with-tshark)
- [For Graphics & Media](#for-graphics--media)
- [For Kernel Boot & System Start-up](#for-kernel-boot--system-start-up)

[Yocto Project](#yocto-project)
  - [Recipe and Meta Layer](#recipe-and-meta-layer)
  - [package management](#package-management)

# Editing in Markdown
1) Install markdown for text to html conversion in your development machine

```
sudo apt-get install markdown
```

2) Write a text file, use _markdown_ to convert to a html page.
Then, use _firefox_ to open the html page.

```
markdown my.text > test.html && firefox test.html
```

3) Some tips for writting markdown

- bullet      : \*, \-
- image       : < img src="pic.png" width="400" height="200" />
- italic      : \_text\_
- bold        : \*\*text\*\*
- escape      : use \\ e.g., my\\\_var\\\_with\\\_underscore
- header      : use \#text, \#\#text, \#\#\#text for 1\-, 2\-, 3\-level header
- linked text : \[My Header\]\(\#my\-header\)

# Networking
## Setting-up /etc/network/interfaces

Please see examples at [docs/network/iper3](docs/network/iperf3.md#11b-setting-ip-address-for-the-2-adapters-at-linux-vm).

## Using ethtool

For more details about using ethtool for getting and setting configuration for network device,
please see [docs/network/ethtool](docs/network/ethtool.md).

# Git and GitHub Setup

## General Overview and Setup for git

git is the de-facto source code management tool widely used in open source projects.
Before you continue to read more about it, you should first setup at your home directory
a default git configuration (~/.gitconfig).

An example of my ~/.gitconfig is shown at [docs/git-setup/gitconfig](docs/git-setup/gitconfig.md).
For time being, you can ignore the "smtpPass = <app password>" in \[sendemail\] as we will see how
to setup your google 2-way password to use 'application password' authentication instead of your
google account user password.

In addition, if you are interested to setup your prompt to automatically print 'git branch' info,
please read [docs/git-setup/git-sh-setup](docs/git-setup/git-sh-setup.md).

## Setting-up SSH Access

Please see [docs/git-setup/ssh-key](docs/git-setup/ssh-key.md)

## Setting-up Github Account

Please see [docs/git-setup/github-setup](docs/git-setup/github-setup.md)

## Setting-up git-pw

A useful script between patches in patchwork and git:
Please see [docs/git-setup/git-pw](docs/git-setup/git-pw.md)


# Performance Gathering
## For Processor

## For I/O Access

## For Networking
### iperf3

For more details about using iperf3 for collecting network throughput and latency,
please see [docs/network/iper3](docs/network/iperf3.md).

### wireshark

This section contains information about wireshark setup and its usage, please see
[docs/network/wireshark](docs/network/wireshark.md)

### Lua Scripting with tshark

For more information how Lua script can be used as dissectors for Wireshark network
packet analyzer console (tshark), please see [docs/network/tshark-lua](docs/network/tshark-lua.md)

## For Graphics & Media

## For Kernel Boot & System Start-up

# Yocto Project

## Recipe and Meta Layer

## Package Management

For more details about how to add package manager, setup package feed and install new
software packages from target machine, please see [docs/yp-dnf](docs/yp-dnf.md)
