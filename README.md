# resolvconf

![Alt text](kodi.png?raw=true "Kodi")

Resolvconf binary

Used to set up VPN connection for Kodi running LibreElec, running on a RasberryPi, using ProtonVPN as a service provider

LibreElec is a minimilized Linux operating system used to exclusively run Kodi. This means that the root file system is read only and it is difficult to add additional applications outside of the Kodi interface.

## Components
 
1) **Openresolv** is an OpenVPN addon to allow for the updating to DNS servers and in particular /etc/resolv.conf - http://roy.marples.name/projects/openresolv/

2) **update-resolv-conf.sh** - https://github.com/alfredopalhares/openvpn-update-resolv-conf This repo contains a "reworked" version of update-resolv-conf.sh. Testing with the original script didn't work

## Steps to install

1) Install the OpenVPN addon for Kodi with the following zip file https://github.com/Zomboided/repository.zomboided.plugins/releases/download/1.0.0/repository.zomboided.plugins-1.0.0.zip

2) Enable ssh access to Kodi

3) ssh onto your Kodi machine

4) 

      mkdir /storage/local
      cd /tmp
      wget https://github.com/RamSailopal/resolvconf/raw/main/resolvconf.zip
      cd /storage/local
      unzip /tmp/resolvconf.zip
      
5) Download the .ovpn files for ProtonVPN using the following guide https://protonvpn.com/support/vpn-config-download/

6) scp the downloaded zip file to the **/tmp** folder of your Kodi machine.

7)    

      mkdir /tmp/ProtonVPN
      cd /tmp/ProtonVPN
      unzip /tmp/ProtonVPN_server_configs.zip
      
8) Set up a User Defined connection in the Kdi OpenVPN addon using the following guide - https://github.com/Zomboided/service.vpn.manager/wiki/09.-User-Defined-VPNs
      Use **/tmp/ProtonVPN** as the location of the opvpn files.
      
9) Amend the imported vpn files with the following command:

        find /storage/.kodi/userdata/addon_data/service.vpn.manager/UserDefined/ -name "*.ovpn" -exec sed -i 's@/etc/update-resolv-conf.sh@/storage/local/sbin/update-resolv-conf.sh@' '{}' \\;
        

## Configuration


There will be two DNS configuration files in **/storage/local/etc**

**VPNDNS.conf** - This file will contain DNS servers when disconnected i.e.
  
**nameserver 8.8.8.8**
   
**NOVPNDNS.conf** - This file will contain "leak proof" DNS servers for when connected i.e.
    
**nameserver 1.1.1.1**
    
Amend the NOVPNDNS.conf file as neccesary for you local network DNS server. 
    

    
      



