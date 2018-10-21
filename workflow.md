# Workflow

## Git Repositories
I access git repositories through ssh with public key authentification
[TODO] I have a cron job that periodically push the local repo to the server, and a script to pull from the repo when I connect and push to the repo when I disconnect. Those jobs use Github deploy keys.

## Projects management
todo_list file in each project
command "todo": show current todo for each project

## Quick access to files and folders
Files and folder for quick access listed in the .shell_files/.quick_access file in their folder or one of their parent folder.
Those .quick_access files generate the necessary files for each shell in the previous .shell_files folder which are called by the shell configuration files.
