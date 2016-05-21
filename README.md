# sbomgr
Bash script to automate installation and updates of packages from SlackBuilds.org.  Works by creating a local copy of the official git repository, running the SlackBuild scripts and reading the other files there, using Slackware's built-in installpkg and removepkg, and querying the list of installed packages in /var/log/packages.  

Initial setup: 
* Set the BRANCH variable near the top of the script as appropriate for the version of Slackware you have installed.  Use 'master' for -current; otherwise, use 14.1, 14.0, 13.37, etc.
* Try 'sbomgr --help' for a list of commands and short descriptions.
* During first use or before checking for upgrades, use 'sbomgr update' to sync your local git repo with the official one.
* sbomgr is intended to be run as root.  You should make it executable and maybe make a symbolic link in /usr/sbin.
