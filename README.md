#port-extended

Copyright 2011 Derek Ashley Thomas

A series of shell scripts are included here to simplify and extend
the capabilities of macports. Macports is an easy to use system
for distributing, compiling, and installing open source software.
[Macports.org](http://www.macports.org/index.php)

My writing of these scripts was motivated by my strong need to keep my
ports synced between devices. It also came in handy when I upgraded my
machine to mountain lion and decided to install all of the ports from
nothing. If there are any bugs, comments, or suggestions feel free to
let me know. Also, you can fork and do with these scripts as you please
in accordance with the license.

The scripts here rely on an environment variable `$LOGS_DIR`, which is
a convenient location to store your shared list of ports. I chose a
subdirectory in Dropbox, but you can choose any syncing system that you
prefer. My only suggestion to the user is that this be a folder that
auto syncs without your input (try iCloud+GoodReader as an alternative).

The following are the included scripts:

* * * * * * * * * * * * * * * * * * * * * * * * * * * * * * 

## pup

This first performs a `port selfupdate`, then it updates outdated ports,
and finally attempts to install new ports that have been installed
on another machine. This script typically requires administrative
privileges unless port was installed in the home directory. To run from
the commandline this means you should use the command:

    sudo pup
    
Upon successful completion, `portupdate` creates a file `$LOGS_DIR/port`
that lists all of the active, installed ports.

After updating, it checks if some expected ports are installed (perhaps
your other machine has them). When this is found, the user is presented
with several options. It tells you which port version/variants are
currently installed and which one is installed on the most recently
updated machine. Then you can request to install or not install, install
with debugger info, `port info`, `port variants`, custom variants, or
even install all the listed ports without any more questions.

Whenever an error occurs, `portupdate` stops so that the user can tell
where a problem is. However, if the "install all" option is selected,
all ports are attempted and errors will not halt the script.

These are very simple functions. They are meant to help keep port
cleanly updated among multiple computers. The script, as it is written
now, assumes that all ports should be synced among all computers. 

## pup-needed

If you run `pup` a log file is generated in the home directory contains
a time stamp of the last successful update. This script reads that
time stamp and determines how many days have passed since the last
full update. A warning is printed if the update occurred more than the
specified number of days ago (default 3 days). You can specify the
cutoff like so:

    # 5 day cutoff
    pup-needed 5 

I have this in my `${SHELL}rc` file (e.g. `.zshrc`) to let me know if my ports get too out of date.

    # check if port needs an update (3 days outdated)
    pup-needed 3

* * * * * * * * * * * * * * * * * * * * * * * * * * * * * * 

## License

GPL 3

Copyright 2011 Derek Ashley Thomas

This file is part of port-extended.

port-extended is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

port-extended is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with port-extended.  If not, see <http://www.gnu.org/licenses/>.
