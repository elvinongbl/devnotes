# Display Git Branch Information Automatically at Command Prompt

PS1 is system variable that defines how your command prompt is printed.
It is evaluated every time shell interpretter completes a command execution.

To enable command prompt to automatically prints git branch information, we
just need to:-

1) Create ~/.git-sh-setup.sh in your home directory with the content in the below link:-

   https://raw.githubusercontent.com/git/git/master/contrib/completion/git-prompt.sh

2) Add the following line to your ~/.bashrc before PS1

```
source ~/.git-sh-setup.sh
```

3) Change PS1 in ~/.bashrc as follow:-

```
PS1='\[\e]2;\u@\H :: \w\a\]\[\e[38;5;39m\]\u\[\e[0m\]@\[\e[38;5;208m\]\H \[\e[38;5;39m\]\W $(__git_ps1 "(%s)") \[\e[38;5;39m\]$ \[\e[0;0m\]'
```

4) Source the newly change ~/.bashrc

```
source ~/.bashrc
```

Goto [main](https://github.com/elvinongbl/devnotes)
