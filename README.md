# raspi-ansible
set up raspberry pi with ansible playbooks

## install headless raspi 
* download https://www.raspberrypi.org/software/
* copy image for distribution Debian or Ubuntu on your SSD card
* copy files from https://github.com/ettenauer/raspi-ansible/headless for selected distribution on SSD card
* insert SSD card into your raspberry pi
* search for your raspberry pi device in local network via nmap
* nmap -sn 192.168.0.0/24 (ip address depends on your NAT)
* download putty (https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)
* connect via putty SSH to your raspberry pi via found ip from nmap command
* default cred: pi and raspberry
* execute sudo raspi-config to update configuration like password etc.

## install ansible on linux deployment host (or ubuntu on windows) with pip
* install pip if not exists
* curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
* sudo python3 get-pip.py -> install global
* python3 -m pip install ansible

## deploy ansible playbooks
* git pull https://github.com/ettenauer/raspi-ansible
* navigate to folder
* update device file with proper device ips or dns names 
* ansible all -i devices -m ping -> verify connectivity
* ansible-playbook 