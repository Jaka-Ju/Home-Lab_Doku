# Chapter 2: The Setup 
## Pi-Hole
### 1. Create a Debian Container or Lubuntu Container 
- Go to local(Pve) <br>
- Upload our downloaded image to ISO Images <br>
- Click create CT in the upper right corner <br>
- You only need to change certain things
    - General
        - Choose a cool name(it's a good practice to name a container something like that name-ct) <br>
        - for our Pi-Hole you have to disable Unprivileged Container <br>
        - Choose a Password (*We need that dont forget it*)
    - Template
        - Choose our Downloaded ISO
    - Disks
        - just choose something 8 or above should be fine 
    - Network (Important)
        - Choose an IP-adress with the modifier static (This will also be your IP to using it as an DNS-Server)
        - You have to write it like this 192.168.172.6/24
        - NO you cant choose 1 or an already used ip. just ping till you find one that doesent respond 
        - Gateway is your chosen ip with a 1 as the last digit, you dont need the /24
    - Activate Autostarting to instantly start our container once the host starts 
### 1.5 Prepare COntainer
- Use the Shell of our Host and type (100 is our container_ID, You most likely need to change that)
    - nano /etc/pve/lxc/100.conf
        - Add this into at the bottom of our file <br>
        lxc.apparmor.profile: unconfined <br>
        lxc.cgroup.devices.allow: c 1:3 rwm <br>
        lxc.cgroup.devices.allow: c 1:5 rwm <br>
        lxc.cgroup.devices.allow: c 1:9 rwm <br>
        lxc.cgroup.devices.allow: c 5:0 rwm <br>
        lxc.cgroup.devices.allow: c 5:1 rwm <br>
        lxc.cgroup.devices.allow: c 10:200 rwm <br>
        lxc.mount.auto: proc:rw sys:rw <br>
    - press ctrl+O
    - press Enter
    - press ctrl+X and quit nano 
- Reboot Container
### 2. Work inside of the Container
- Log in with root and your password 
- Update your Container with, apt update && apt upgrade -y
- Install Curl, apt install curl -y
- Use Curl to install Pi-Hole, curl -sSL https://install.pi-hole.net | bash oder wget -o basic-install.sh https://install.pi-hole.net

### 3. Pi-Hole configuration
- Follow the installation and write down your webinterface data
- Log into the Site with your given Data
- Add Blocklists like these
    - https://raw.githubusercontent.com/StevenBlack/hosts/master/alternates/porn/hosts		
    - https://raw.githubusercontent.com/hagezi/dns-blocklists/main/hosts/pro.plus.txt		
    - https://phishing.army/download/phishing_army_blocklist.txt		
    - https://mirror1.malwaredomains.com/files/justdomains
- Update our Pihole with this command, pihole -g inside of our container 

### 4. Connect to PiHole