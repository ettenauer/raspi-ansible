# raspi-ansible
set up raspberry pi with ansible playbooks

## install headless raspi 
* download https://www.raspberrypi.org/software/
* configure addtional settings by pressing crtl + shift + x
* enabled Wifi and set SSID, Password and Country
* enable SSH and select via Public-Key and copy your SSH public key into the field (required for ansible deployement as well)
* click save and continue to burn image for distribution Debian or Ubuntu on your SSD card
* insert SSD card into your raspberry pi
* search for your raspberry pi device in local network via nmap
* nmap -sn 192.168.0.0/24 (ip address depends on your NAT)
* download putty (https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)
* go to SSH Auth and select your private key for SSH connection
* connect via putty SSH to your raspberry pi via found ip from nmap command

## install ansible on linux deployment host (or ubuntu on windows) with pip
* install pip if not exists
* curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
* sudo python3 get-pip.py -> install global
* python3 -m pip install ansible

## configure hosts and SSH for deployment
* update device, set hosts with ansible_ssh_private_key_file location (ssh key used for headless setup)

## deploy ansible playbooks
* git pull https://github.com/ettenauer/raspi-ansible
* navigate to folder
* ansible all -i devices -u pi -m ping -> verify connectivity
* ansible-playbook 