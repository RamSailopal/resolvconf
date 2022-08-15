# resolvconf

Resolvconf binary

Used to set up VPN connection for Kodi running LibreElec, running on a RasberryPi

LibreElec is a minimilised Linux operating system used to exclusively run Kodi. This means that the root file system is read only and it is difficult to add additional applications outside of the Kodi interface.

# Components
 
1) **Openresolv** is an OpenVPN addon to allow for the updating to DNS servers and in particular /etc/resolv.conf - http://roy.marples.name/projects/openresolv/

2) **update-resolv-conf.sh** - https://github.com/alfredopalhares/openvpn-update-resolv-conf This repo contains a "reworked" version of update-resolv-conf.sh. Testing with the original script didn't work

# Steps to install

1) Enable ssh access to Kodi

2) ssh onto your Kodi machine

3)    mkdir /storage/local

4)    cd /tmp
     
      wget https://github.com/RamSailopal/resolvconf/raw/main/resolvconf.zip



