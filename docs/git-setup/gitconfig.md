# ~/.gitconfig setup

An example of ~/.gitconfig is as shown below:-

```
[user]
 email = elvinongbl@gmail.com
 name  = Ong Boon Leong
 username = elvinongbl

[sendemail]
 from = "Ong Boon Leong <elvinongbl@gmail.com>"
 smtpServer = smtp.gmail.com
 smtpUser = elvinongbl@gmail.com
 smtpEncryption = tls
 smtpServerPort = 587
 smtpPass = <app password>
 signedoffcc = false
 suppresscc = all
 chainreplyto = false
 assume8bitEncoding = utf-8
 confirm = always

[web]
 browser = google-chrome
[instaweb]
 httpd = apache2 -f

[color]
 diff = auto
 ui = auto
 interactive = auto
 grep = always

 [color.branch]
 current = green
 local = white
 remote = red
 upstream = yellow
 plain = white

[color "grep"]
 match = red

[core]
 editor = vi
 # gitproxy = /home/bong5/common/bin/socatproxy
 whitespace = trailing-space,tab-in-indent
 pager = sed 's/\t/>-------/g' | less -R

[alias]
 co = checkout
 dc = describe --contains
 br = branch -v
 ci = commit
 st = status
 stsb = status -sb
 ol = log --oneline
 cp = cherry-pick
```

# Setup gmail for git send-email

In order to use gmail for sending patch series to mailing list, you need to:-
a) At your account setting, turn-on 2-Step Verification which is by default disabled
b) Then, create App password specific for your machine and git application
c) Replace the generated hash value and put it into smtpPass = <app password> in ~/.gitconfig

Goto [main](https://github.com/elvinongbl/devnotes)
