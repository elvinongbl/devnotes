# Setting up git-pw (cmd that bridges git & patchwork)

## Introduction
There are two versions of patchwork in the industry:-

A) The original:
   - https://github.com/getpatchwork/patchwork
   - https://github.com/getpatchwork/git-pw

B) The Freedesktop version:
   - https://gitlab.freedesktop.org/patchwork-fdo/patchwork-fdo/
   - https://gitlab.freedesktop.org/patchwork-fdo/patchwork-fdo/tree/master/git-pw

Due to historical reason, the patchwork for these versions are not compatible and the respective
git-pw is not compatible too:-

- For Linux netdev: please use (A).
  -- The patchwork website: https://patchwork.ozlabs.org/project/netdev/list/
- For Linux intel-gfx: please use (B).
  -- The patchwork website: https://patchwork.freedesktop.org/project/intel-gfx/list/

## Steps to install the original 'patchwork' git-pw

1) Install python modules
```
sudo apt-get install python-requests python-click python-pbr python-arrow python-tabulate
```

2) Getting git-pw
```
cd ~/repos
git clone https://github.com/getpatchwork/git-pw
cd git-pw
sudo python setup.py install
```

3) Check git-pw is working by showing the default help
```
git pw
```

4) Get Linux net-next repo
```
git clone git://git.kernel.org/pub/scm/linux/kernel/git/davem/net-next.git
or
git remote add net-next git://git.kernel.org/pub/scm/linux/kernel/git/davem/net-next.git
git fetch net-next
git checkout -b net-next --track net-next/master
```

5) Register an account with https://patchwork.ozlabs.org/ & obtain the token from 'view profile' button on top-right of you login page.

6) Setup ~/.gitconfig patchwork setting
```
[pw]
server = https://patchwork.ozlabs.org/api/1.1
project = https://patchwork.ozlabs.org/project/netdev/list/
token = <my-token>
username = <my-login>

```
7) Finally, try interact with patchwork server through below commands
```
git pw patch list <keywords>
git pw series list <keywords>
git pw series show <id>
git pw series download <id>
git pw series apply <id>
```

Goto [main](https://github.com/elvinongbl/devnotes)
