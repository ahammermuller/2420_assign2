# AlineHammermuller

# How to set up a Load Balancer, a Firewall, a Web Server and apply some basic configuation trough Digital Ocean
 
## Digital Ocean droplet

1. Create an accout at Digital Ocean (https://www.digitalocean.com/)
	Could be the most basic account.
2. Open Windows terminal to generate and ssh key by typing ssh-keygen
3. Enter file in which to save the key (for exemple /Users/USER/.ssh/id_rsa)
	Change the name of the key (id_rsa) for another one related to the project
4. Enter passphrase (empty for no passphrase). Repeat the passphrase.
	If you wish you could just leave it empty.
5. Copy the public key using the command: cat ~/.ssh/<key.name>.pub
	Where <key_name> is the name given for your key in step 3.
6. Login at Digital Ocean, go to Settings (left menu) - Scurity - Add SSH Key
7. Paste de key and give it a meningful name.
8. Create a new project if do not have one or a new droplet if you already have a project
9. Select to use the primary key that you already created in your new droplet.

**Remeber to give your project a tag. You will use this same tag on your droplet, load balancer and firewall

## Digital Ocean Load Balancer

1. On the left side menu click on Networking
2. Click on the tab Load Balancers
3. Click on the button Create Load Balancer
4. Choose a datacenter region (the same that you used to create your droplet)
5. Connect droplets using a tag (the same tag that you used in your droplet)  
6. Click on the button create and you will be able to see your droplets in the load balancer.

## Digital Ocean Firewall

1. On the left side menu click on Networking
2. Click on the tab Firewalls
3. Click on the button create firewall
4. Give your firewall a name
4. As inbound rules keep SSH selected and select HTTP too. 
5. On HTTP field sourcers type load and select your load balancer
6. Again specify the tag to connect the droplets, load balancer and firewall. 
7. Click on the button create firewall

## Create a new user on droplet

1. Open a windows terminal on the host machine
2. Type ssh root@\<ipv4 address of your droplet>
3. Type adduser \<usernsme>

<img src=./images/adduser.jpg width="500">

## Install Caddy(Web Server) in both droplets

To install Caddy login using ssh at your droplets.
Type the following commands:

> sudo apt install -y debian-keyring debian-archive-keyring apt-transport-https
> 
> curl -1sLf 'https://dl.cloudsmith.io/public/caddy/stable/gpg.key' | sudo gpg --dearmor -o /usr/share/keyrings/caddy-stable-archive-keyring.gpg
>
> curl -1sLf 'https://dl.cloudsmith.io/public/caddy/stable/debian.deb.txt' | sudo tee /etc/apt/sources.list.d/caddy-stable.list
> 
> sudo apt update
> 
> sudo apt install caddy

Installing Caddy using apt install, this way Caddy apt will kepp Caddy up-to-date.

## Write a web app

1. Login inside you wsl using windows terminal
2. Create a directory (in my case I named it 2420-assign-two)
3. Inside this directory create two other directories named html and src
4. Inside the html directory create an index.html page
5. Download nodejs from https://nodejs.org/en/
6. 
