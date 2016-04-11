# Seths guide to setting up your UNRAID server
After working with unraid for several years, I decided its time I documented things I learned and how my current setup works. While I do intend for this guide to help others, honestly, I'm doing this documentation just as much for my own purposes, as I have trouble remembering all the tricks I used in the setup process.

## Table of Contents
- [Building or Buying an UNRAID Server] *...todo*
- [Downloading and Installing the OS](#downloading-and-installing-the-os)
- [Configuring your UNRAID server for the first time] *...todo*
- [Setup Deluge Torrent with VPN for Security](#setup-deluge-torrent-with-vpn-for-security)
- [Setup CouchPotato] *...todo*
- [Setup Sabnzb] *...todo*
- [Setup Sonarr] *...todo*
- [Setup Plex] *...todo*
- [Setup NoIP] *...todo*

## Downloading and Installing the OS
- https://lime-technology.com/download/
- I highly recommend you just purchase the prebuilt flash drive from limetech to avoid any setup issues:
- [https://lime-technology.com/preconfigured-usb-flash/](https://lime-technology.com/preconfigured-usb-flash/?refer=sethcarstens)
- `TODO: guide on setup of server`

<img src="https://raw.githubusercontent.com/scarstens/unraid-setup/master/assets/unraid-dashboard-v6-example1.png" width="500">

## Setup Deluge Torrent with VPN for Security
This setup assumes you are going to pay for privateinternetaccess.com to protect your privacy while using a torrent provider, and that your local network is setup to DHCP addresses like '192.168.2.1`. Note that deluge is more reliable then transmission, utorrent or rtorrent when you are using the UNRAID, Docker and related media providers (like couchpotato, sonarr, sickbeard, etc). 

- Signup and pay for account at privateinternetaccess.com
- From unraid web GUI -> docker -> search `binhex-delugevpn` and install
- Click `advanced` toggle in unraid ui (top right) 

![unraid-docker-advanced-view](https://raw.githubusercontent.com/scarstens/unraid-setup/master/assets/unraid-docker-advanced-view.png "unraid-docker-advanced-view")

- Change the ENV parameters as follows:
    - create `LAN_NETWORK` = `192.168.2.1/0`
    - edit `VPN_USER` = [GetFromPIA](privateinternetaccess.com?refer=sethcarstens)
    - edit `VPN_PASS` = [GetFromPIA](privateinternetaccess.com?refer=sethcarstens)
    - edit `ENABLE_PRIVOXY` = `yes`
    - edit `LAN_RANGE` = `192.168.2.1-192.168.2.254`
- manually add new deluge client user and password so other docker containers can authenticate (http://dev.deluge-torrent.org/wiki/UserGuide/ThinClient#AddUsertotheauthenticationfile) I did this by `ssh` into the box and then editing the auth file, paths may vary depending on your config, mine looked like this `sudo nano /mnt/cache/appdata/binhex-deluge-vpn/auth` which opens the file for edit, then you just add `deluge:deluge:10` which will allow all docker apps on your server to authentication with deluge via the username `deluge` and the password `deluge`
- Stop and then Start the deluge docker

*Click to enlarge image:*

<img src="https://raw.githubusercontent.com/scarstens/unraid-setup/master/assets/unraid-docker-deluge-settings-example1.png" width="300">
