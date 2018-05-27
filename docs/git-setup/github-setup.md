# Setup Github project

1) After you have setup your SSH public key with your GitHub account, please
make sure that you choose "Clone with SSH" instead of "Clone with HTTPS". This
prevents you from entering username and password everytime you need to push
commits back to GitHub repositories.

<img src="../images/clone-with-ssh.png" width="400" height="200" />

The URL for the git clone should look like below:
```
git@github.com:<user-name>/<project-name>.git
```

If you are not sure, how to check the URL that you have used before in other
repositories, you can use below command to check out:-

```
git remote -v
```

2) If you have done "git clone" by using https protocol, you can set the new url
for your named repository with ssh as follow
```
git remote set-url <named-repo> git@github.com:<user-name>/<project-name>.git
```

2) To allow other contributors to be able to push to GitHub repositories,
in respective project "settings" page and choose collaborators tab for add their
GitHub account names there.

Goto [main](https://github.com/elvinongbl/devnotes)
