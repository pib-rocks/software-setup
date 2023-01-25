# software-setup

Prepare and install a Raspberry Pi 4 which is freshly installed with Ubuntu 22.04 server (64bit) with ROS2

IMPORTANT: Use the 64bit version of Ubuntu 22.04. ROS2 can't be installed on the 32bit version!

## Setup:

- Edit hosts.ini:
  - Replace `<your_raspberrypi_fqdn>` with 
    - the full qualified domain name if your DNS is working 

    OR

    - the IP address

  of your freshly installed raspberry pi

- Edit `host_vars/pib/firstrun.yml`
  - Replace `<your_raspberrypi_username>` with the username you used for preparing your SD card for the pi with rpi-imager

- Copy your ssh key to `templates/ssh.key`

## Prepare the raspberry pi for the ansible setup:

- Run the following command:
  
  `ansible-playbook --inventory-file hosts.ini firstrun.yml -l pib --ask-pass --ask-become-pass`

  and enter the password for your user on the raspberry pi and another enter as the passwords will be the same.

## Install ROS2 to your raspberry pi:

- Run the following command:

  `ansible-playbook --inventory-file hosts.ini ros2.yml -l pib`

  This time everything should be automatically done.

## Check installation

Afterwards log into your raspberry pi and check with the follwoing commands:

  `echo $ROS_DISTRO`

  `ros2`

## Additonal 

If you want to install ROS2 to your Linux Mint desktop machine with Version 21.1 or Ubuntu-22.04

  - Replace <your_desktop_fqdn> with the full qualified domain name of your desktop machine or IP address in `hosts.ini`
  - Replace <your_desktop_username> with the username you use on your desktop machine in `host_vars/desktop/firstrun.yml`

### Prepare desktop machine for the ansible setup (if needed):

- Run the following command:

  `ansible-playbook --inventory-file hosts.ini firstrun.yml -l desktop --ask-pass --ask-become-pass`

  and enter the password for your user on your desktop machine and another enter as the passwords will be the same.

## Install ROS2 to your raspberry pi:

- Run the following command:

  `ansible-playbook --inventory-file hosts.ini ros2.yml -l desktop`

  This time everything should be automatically.

## Check installation

Afterwards check on your desktop machine with the follwoing commands:

  `echo $ROS_DISTRO`

  `ros2`

