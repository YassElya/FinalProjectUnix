# Installation
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
