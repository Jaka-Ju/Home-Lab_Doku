# Chapter 2: The Setup 
## Pi-Hole
### 1. Create a Debian Container 
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

### 2. Work inside of the Container