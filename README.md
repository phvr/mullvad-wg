# Mullvad WireGuard script  <img src="https://slethen.io/content/images/2017/01/mullvad-logo.png" align="left" width="40" height="40" alt="logo">
Simple script that makes it easier to use Mullvad's VPN with WireGuard and OpenRC on Gentoo.
Forked from Adi Hrustic

<img src="https://i.imgur.com/QqBj2Rm.gif" align="right" alt="gif" width="515" height="412">


## Prerequisites
* [Mullvad Account](https://mullvad.net/)
* Gentoo Linux
* A kernel able to run WireGuard

## Installation
Install phvr-overlay and do
```
# emerge -a mullvad-wg
```

## Usage

### Configuring the servers
To pull in all available servers and their wireguard configs, do
```
mullvad update servers
```
This will prompt you for your Mullvad account number.
Do this after installation.

### Connecting to a server
To connect to a server, simply write
```
mullvad connect <server>
```

It it also possible to leave out server selection and connect to default
```
mullvad connect
```

Note that this needs to be set with `mullvad update default`, before using the above command.

### Disconnecting from a server
```
mullvad disconnect
```

### Updating default server
```
mullvad update default
```
This command will let you set a default server of your choosing. Use the `list` command to view the current default.

### Enabling/Disabling kill-switch
Enable a kill-switch
```
mullvad kill-switch on <server>
```

Disable a kill-switch
```
mullvad kill-switch off <server>
```

It is possible to choose multiple servers. To enable a kill-switch for all servers run
```
mullvad kill-switch <on|off> all
```

### Listing servers
When you first update the server list you will shown the current available servers. To view the list again type
```
mullvad list
```

### Status of current connection
To get more detailed information about your connection, run
```
mullvad status
```
or
```
mullvad verify
```
to verify using the am.i.mullvad.net API

### Choosing start-up server
It is possible to choose a server that will auto connect on boot.
```
mullvad start-up <on|off> <server>
```
Show the currently selected startup server:
```
mullvad start-up show
```
For this to work you need the 'local' service enabled:
```
# rc-update add local default
```

### Help
The help section can be accessed with
```
mullvad help
```

## More information
* [Running WireGuard with Mullvad on Linux](https://mullvad.net/en/guides/wireguard-and-mullvad-vpn/) - Mullvad's official guide.
* [WireGuard](https://www.wireguard.com/) - Official WireGuard website.

## Authors
Adi Hrustic wrote this script - phvr forked it to adapt it to OpenRC and package it for Gentoo

## License
This project is licensed under the GNU General Public License v3.0 - see the [LICENSE.md](LICENSE.md) file for details.
