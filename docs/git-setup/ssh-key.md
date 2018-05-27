# Setting-up SSH key

1) Install openssh-client & ssh-agent-filter
```
sudo apt-get install openssh-client ssh-agent-filter
```

2) Generate Your SSH key
```
ssh-keygen -t rsa -b 4096 -C "<somename>@<company.com>"
```
Note: the generated key are usually stored under ~/.ssh/

3) Register Your SSH public key with the server

Login into the account of where git repositories are hosted
and populate the public key from below output
```
cat ~/.ssh/id_rsa.pub
```

4) Test Your service access
```
ssh -T <user>@<server.com>
```

5) Start ssh-agent
```
eval $(ssh-agent -s)
```

6) Add private key to ssh-agent
```
ssh-add ~/.ssh/id_rsa
```

7) Check SSH_AUTO_SOCK and SSH_AGENT_PID are valid
```
echo ${SSH_AUTO_SOCK}
echo ${SSH_AGENT_PID}
```

Further read: github.com provides good SSH setup documentation.
Start with [GitHub SSH Setup](https://help.github.com/articles/connecting-to-github-with-ssh/)

Goto [main](https://github.com/elvinongbl/devnotes)
