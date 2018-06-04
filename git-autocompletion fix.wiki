https://github.com/bobthecow/git-flow-completion/wiki/Update-Zsh-git-completion-module


Ubuntu
Replace /usr/share/zsh/functions/Completion/Unix/_git with the latest version available here: _git
https://raw.githubusercontent.com/zsh-users/zsh/master/Completion/Unix/Command/_git

Mac OS X
Replace /usr/share/zsh/x.x.xx/functions/_git with the latest version available here: _git
https://raw.githubusercontent.com/zsh-users/zsh/master/Completion/Unix/Command/_git

Notes
I have no idea when this file is loaded. You may need to logout/login to get flow completion working.
Flow completion only functions after you have typed "git flow" (e.g., "git fl<tab>" will expand to git reflog, while "git flow fe<tab>" will expand to git flow feature).
