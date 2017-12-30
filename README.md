# sbomgr

Deprecation notice
================================================================================
After version 0.6.0, sbomgr will be merged into [sboui](https://github.com/montagdude/sboui) as sboui-backend. No more commits will occur in this repository. If you wish to keep using sbomgr, it is recommended to install sboui instead. sboui-backend can still be used from the command line just like sbomgr, or you can take advantage of the sboui frontend as well, which provides many additional features.

Overview
================================================================================
sbomgr is a tool to automate installation of packages from SlackBuilds.org (SBo) or other git-based SlackBuild repositories. It works by cloning the SBo git repository and running the SlackBuild scripts along with upgradepkg and removepkg. It is meant to be simple and light; it does not resolve dependencies or attempt to decide for you which packages should be upgraded (or even keep track of that). However, it pairs naturally with sboui to add these features and many more (see section below for more details).

Installation
================================================================================
A SlackBuild script is available for sbomgr here:

https://github.com/montagdude/SlackBuilds/tree/master/system/sbomgr

You can either clone the whole repository and navigate to SlackBuilds/system/sbomgr, or you can download the individual files with the "Raw" link on the github web interface. Before running the SlackBuild script, download the source from the link in the .info file. The SlackBuild script creates a Slackware package which can be installed using installpkg.

Usage
================================================================================
sbomgr usage is fairly self-explanatory. The update command creates and/or syncs the local repository with the git origin. The install command builds and installs a package, and the remove command removes it. For a full list of options, try `sbomgr --help`. Before running sbomgr for the first time, please take time to view and edit the configuration file, /etc/sbomgr/sbomgr.conf, to your liking.

Use with sboui
================================================================================
sboui is an ncurses user interface for sbopkg, sbotools, and other SBo package managers providing many useful extensions and enhancements, including dependency resolution, powerful and fast searching and filtering, tagging and applying batch changes, and blacklisting. It can be found on SlackBuilds.org or at the following location on github:

https://github.com/montagdude/sboui

To use sbomgr as the backend for sboui, use the following settings in /etc/sboui/sboui.conf:
* package_manager = "custom"
* sync_cmd = "sbomgr update"
* install_cmd = "sbomgr install -f"
* upgrade_cmd = "sbomgr install -f"
* repo_dir = ($CDIR, as defined in /etc/sbomgr/sbomgr.conf)

Use with non-SBo repositories
================================================================================
sbomgr can also be used to manage non-SBo repositories, by taking these steps:
* Create a new configuration file with variables reflecting the repository you want to use.
* Run sbomgr as follows: CONF=/path/to/custom/config/file sbomgr COMMAND [OPTIONS] [SLACKBUILDS]
* The repository should be organized similarly to SBo; i.e., top-level/group/package structure.
* SlackBuilds should follow SBo guidelines; i.e., must have .SlackBuild, .info, slack-desc, README, etc.
