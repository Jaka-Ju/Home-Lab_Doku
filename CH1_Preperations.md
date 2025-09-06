# Chapter 1: The preperations 
## Get Hardware   | My Setup <br>
- RAM        : 16 Gigabyte<br>
- Core       : 4<br>
- Threads    : 4<br>
- Diskspace  : 512 Gigabyte <br>

## Setup Proxmox
- Prepare a bootable USB-Stick with Proxmox in Rufus
- You can Connect via your browser just type: The IPadress:8006/ <br>
-8006 is a certain port <br>

## Get ISO        | What I chose
- I chose Debian 12  netinst, for 64-bit PC (amd64) debian-13.0.0-amd64-netinst.iso.<br>
- I also chose ubuntu -22.04 because not like debian it actually works for Pihole <br>
- This Iso will be the Backbone of nearly all VM or Containers.<br>
### Warning Debian isnt always chooseable, you need to downlad it in Proxmox CT-Templates --> Templates and choose it there <br>
## What I am installing and why
- Pi-Hole (DNS-Server) because I hate ads and dont want to get sketchy advertisments <br>
- WireGuard (VPN-Tunnel) to access my Server from the outside without exposing it to the potential attackers <br>
....<br>

