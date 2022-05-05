# Installation
- [VPS Installation](#VPS-Installation)
- [SSH Key](#SSH-Key)
- [Connecting to the remote server](#Connecting-to-the-remote-server)
- [Upgrade & Update](#Upgrade--Update)
- [Create a new user](#Create-a-new-user)
- [Security](#Security)
- [Installing video streaming & Hosting](#Installing-video-streaming--Hosting)
- [Q&A](#Q-&-A)
## VPS Installation
- create an account on OVHcloud.
- create a new virtual private server (VPS) by navigating on bare metal cloud.
- Select Ubuntu 20.04 or any other versions you want.
- In our project, we pick a plan with 2GB CPU with 40 GB transfer.
- Choose a data center region
  - We choose Beauharnois(BHS) because it is the nearest one.
- Authentication
  - There are two ways: [SSH key](#ssh-key) or one time root password
  - For the purpose of this project we used one time password but in the future it is better to use SSH key. It offers more security.
- Assign a host name
  - we named ours  Virtual streaming server.
- IP address
  - After the verification is finished, you'll obtain an IP address that you can SSH to your vps. You can connect using this "ssh root@IP_ADDRESS".
## SSH Key
-   If you want to use SSH key and you do not have it, Follow this instruction.
    - Linux Environment:
     - Create a directory using `$ mkdir ~/.ssh` if it doest not exist already.
      - `$ ssh-keygen -b 4096` running this command will create your rsa key. The `-b 4096` indicates the size. Then enter to confirm the default location.
      - Use `cat ~/.ssh/id_rsa.pub` to check your public key.
      - Copy its content to digital ocean ssh authentication.
      - Use this key when you connect to the remote server.
    - Windows
     - To generate your ssh key on windows platform you have to use PuTTY. Check [this][PuTTY] for installation guide
## Connecting to the remote server
- Connect to the server using the provided ip address
  - On windows 
    -Open command prompt
    -type `$ ssh root@IP_ADDRESS`
    -enter your key or password
  - On linux
    -Open terminal
    -type `$ ssh root@IP_ADDRESS`
    -enter your key or password
## Upgrade & Update
- Before we create a new user we have to update and upgrade our system
- run these commands:
  - `sudo apt-get update`
  - `sudo apt-get upgrade`
    -press y to confirm the upgrade

## Create a new user
 - After successfully connecting to the server, you create a new account in order to not run every command in the root.
    - `useradd username` will add new user
    - `usermod -aG sudo username` add the user to the sudo group
    - `groups username` to verify if the user is successfully added to the sudo group.
    - `su username` to switch to the other user.
    - try to logout from the server and connect to it again using the new user.
## Security
- Since we are hosting a video streaming server, we want to make sure that our VPS will be protected from all threats so that people will not hack into our system and disable access to the root.
  -First, "sudo passwd -d root" this will disable the password for root. 
  - We added the apt-get install fail2ban
  - cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.conf.backup, this will print unknown IP addresses to 
penetrate the system. 
## Installing video streaming & Hosting
-Open the terminal:
 [installin the game "7Days to Die"](https://linuxgsm.com/servers/sdtdserver/)
 - run the command  adduser sdtdserver
 - su- sdtdserver
 - run this command in your terminal to allow you to have access to different video streaming games: wget -O linuxgsm.sh hhttps://linuxgsm.sh && chmod +x linuxgsm.sh && bash linuxgsm.sh sdtdserver
 
 [Also, we added Nginx:](https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-ubuntu-18-04)
- `sudo apt install nginx` to install nginx
- `systemctl status nginx` checkig the status of nginx 
- In your browser, type in your IP address and you should see the nginx welcome message.

## Q&A
### if you cannot connect to VPS?
- just check the internet connection first.
- Make sure you have the correct IP address.
- Make sure you have the correct key or password
### My website is not loading?
- check the status of nginx if it is running systemctl nginx status.
- Make sure your video streaming apps are in added in right directory.
### If ssh is not working?
- Log in to root to configure the ssh keys using the sudo group users.
- try installing openssh-server using this command `sudo apt install openssh-sever.
### If the ip address is long and have complicate values?
- In order to change your ip address to the one of your preference, you meed to have a domain using websites like scalahosting 
that have managed VPS and gives an option of buying a domain to customize your IP address.
### when the connection is timed out on port 22?
You need to make sure that you allowed ssh connection on this port. You can fix this by logging in to your OVHcloud account and go to the Bare Metal Cloud and type sudo allow 22.
### Is it necessary to stay in root user?
- Login in to the server and create another user, then add it to the sudo group.
- useradd username is the command we used to add new user.
- sudo usermod -aG sudo "username" adds the user you created to the sudo group.
- groups username to verify if the user is successfully added to the sudo group.
- su username switches to other users.
