# sbomgr
sbomgr is a tool to automate installation of packages from SlackBuilds.org (SBo) or other git-based repositories of SlackBuilds. It works by cloning the SBo git repository and running the SlackBuild scripts along with installpkg and removepkg.  It also keeps track of installed SBo packages, lists dependencies and inverse dependencies, searches and shows information about packages, and more. For a list of available options, just type 'sbomgr' or 'sbomgr --help'. Before first use, be sure to run 'sbomgr update' to sync the local git repository with the official one.

Parameters can be edited in the configuration file /etc/sbomgr/sbomgr.conf. Use this file to set the Slackware release and other options.

SlackBuild scripts are available at: https://github.com/montagdude/SlackBuilds/sbomgr

sbomgr can also be used to manage non-SBo repositories, by taking these steps:
* Create a new configuration file with variables reflecting the repository you want to use.
* Run sbomgr as follows: CONF=/path/to/sbomgr.conf sbomgr COMMAND [OPTIONS]
* The repository should be organized similarly to SBo; i.e., top-level/group/package structure.
* SlackBuilds should follow SBo guidelines; i.e., must have .SlackBuild, .info, slack-desc, README, etc.
