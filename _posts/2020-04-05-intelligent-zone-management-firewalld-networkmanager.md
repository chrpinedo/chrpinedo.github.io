---
layout: post
title: "Intelligent firewall zone management with firewalld and NetworkManager"
category: Technology
tags:
- firewall
- firewalld
- networkmanager
- linux
---

In my ArchLinux laptop I use firewalld as firewall manager application. It provides a firewall configuration based on zones and I use many of them such as public, trust, home or work depending where I am connected to. Furthermore, I use NetworkManager to manage all my available network connections: ethernet, WiFi, VPN...

There is some kind of integration between firewalld and NetworkManager. You can define that a NetworkManager connection is assigned to one zone. This is quite good for wireless, VPN connections and static ethernet connections. However, it is not sufficient for the ethernet connection of a mobile device such as a laptop because the ethernet DHCP connection should be assigned to different firewall zones if you connect the laptop at work or at home, for example.

One solution I used until now was to define multiple "Ethernet-DHCP" connections in NetworkManager to apply them to different security zones (for example, "Home-DHCP" connection to apply the home zone of firewalld, "Work-DHCP" to apply the work zone, "Public-DHCP" to apply the public zone...). The big handicap of this solution is that you can only have one ethernet connection in NetworkManager as default. This is the default connection applied to the interface and it should be the most secure by default, the public connection. Then if you are at work or at home, you need to remember to change your connection in NetworkManager to apply the correct firewall zone to the interface. I usually am connected at home, so it is quite annoying to have to manually change the firewall zone.

I found an elegant solution during this confinement due to Covid-19. I have only one DHCP connection for the ethernet interface of my laptop and I created one script to use with NetworkManager dispatcher to change dynamically the firewall zone assigned to the interface. The script is simple. When the interface and the connection is up, the script is executed by NetworkManager. The script pings the IP address of my home router and check its MAC address. If the MAC address is the MAC address of my home router, I am at home and the interface is assigned to home zone. If not, the public zone is applied. 

```bash
#!/bin/sh

ETH_CONN="d5078ee7-e148-3667-b647-393931d6e838"
ETH_IF="enp0s25"
HOME_GW_IP="192.168.0.1"
HOME_GW_MAC="00:0c:42:aa:bb:cc"

if [ "$CONNECTION_UUID" = "$ETH_CONN" ]; then
	case "$2" in
		up)
			# if we are at home network....
			ping -c 1 "$HOME_GW_IP"
			if arp -n "$HOME_GW_IP" | grep -q "$HOME_GW_MAC" ; then
				firewall-cmd --permanent --change-zone="$ETH_IF" --zone=home
			else
				firewall-cmd --permanent --change-zone="$ETH_IF" --zone=public
			fi
			;;
		down)
			# reset again to the public zone...
			firewall-cmd --permanent --change-zone="$ETH_IF" --zone=public
			;;
	esac
fi

```




This script can also be extended with the IP and MAC addresses of routers of other networks and so we can manage dynamically the firewall zone of the ethernet interface of our laptop.
