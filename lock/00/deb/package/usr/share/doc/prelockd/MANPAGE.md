% prelockd(8) | Linux System Administrator's Manual

# NAME
prelockd - Daemon that locks memory mapped binaries and libraries in memory to improve system responsiveness under low-memory conditions.

# SYNOPSIS
**prelockd** [**OPTION**]...

# DESCRIPTION
prelockd is a daemon that locks memory mapped binaries and libraries in memory to improve system responsiveness under low-memory conditions.

# COMMAND-LINE OPTIONS

#### -c CONFIG
path to the config file

# FILES

#### :SYSCONFDIR:/prelockd.conf
path to configuration file

#### :DATADIR:/prelockd/prelockd.conf
path to file with *default* prelockd.conf values

# HOW TO CONFIGURE
Edit the config and restart the service.

# REPORTING BUGS
Feel free to ask any questions and report bugs at <https://github.com/hakavlad/prelockd/issues>.

# AUTHOR
Written by Alexey Avramov <hakavlad@gmail.com>.

# HOMEPAGE
Homepage is <https://github.com/hakavlad/prelockd>.
