[Getting Started](https://github.com/AdguardTeam/AdGuardHome#getting-started)
[Automated install (Linux/Unix/MacOS/FreeBSD/OpenBSD)](https://github.com/AdguardTeam/AdGuardHome#automated-install-linux-and-mac)
To install with curl run the following command:

curl -s -S -L https://raw.githubusercontent.com/AdguardTeam/AdGuardHome/master/scripts/install.sh | sh -s -- -v
To install with wget run the following command:

wget --no-verbose -O - https://raw.githubusercontent.com/AdguardTeam/AdGuardHome/master/scripts/install.sh | sh -s -- -v
To install with fetch run the following command:

fetch -o - https://raw.githubusercontent.com/AdguardTeam/AdGuardHome/master/scripts/install.sh | sh -s -- -v
The script also accepts some options:

-c <channel> to use specified channel;
-r to reinstall AdGuard Home;
-u to uninstall AdGuard Home;
-v for verbose output.
Note that options -r and -u are mutually exclusive.