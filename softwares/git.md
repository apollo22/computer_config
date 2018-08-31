# Git

## Github

When using Github, I almost always use **public key authentification**.

[TODO] My files are synchronised when I login, when I logout, and every hour (except if I am on a metered connection

When pushing to the github repo, I use a github deploy key for each repository. I can specify the location of the linked private key in two ways:
  - execute 'git config core.sshCommand "ssh -i <path/to/file>"' in the git folder
  - add "sshCommand = ssh -i <path/to/file>" in the git config file (<repo>/.git.config), under [core]
