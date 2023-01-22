# software-setup

Prepare and install a Raspberry Pi 4 which is freshly installed with Ubuntu 22.04 server with ROS2

## Setup:

- Edit hosts.ini:
  - Replace <your_raspberrypi_fqdn> with the full qualified domain name of your freshly installed raspberry pi

- Edit host_vars/pib/firstrun.yml
  - Replace <your_raspberrypi_username> with the username you use on your raspberry pi (default might be pi)

## Prepare the raspberry pi for the ansible setup:

- Run the following command:
  
  ansible-playbook --inventory-file hosts.ini firstrun.yml -l pib --ask-pass --ask-become-pass

  and enter the password for your user on the raspberry pi and another enter as the passwords will be the same.

## Install ROS2 to your raspberry pi:

- Run the following command:
  ansible-playbook --inventory-file hosts.ini ros2.yml -l pib

  This time everything should be automatically.

## Check installation

Afterwards log into your raspberry pi and check with the follwoing commands:

  echo $ROS_DISTRO
  ros2

## Additonal 

If you want to install ROS2 to your Linux Mint desktop machine with Version 21.1

  - Replace <your_desktop_hostname> with the hostname of your desktop machine
  - Replace <your_desktop_fqdn> with the full qualified domain name of your desktop machine
  - Create a directory in host_vars with the hostname of your desktop machine
  - Copy the file from host_vars/pib to this new directory and adjust their content
    - Replace <your_raspberrypi_username> with the username you use on your desktop machine

### Prepare desktop machine for the ansible setup (if needed):

- Run the following command:

  ansible-playbook --inventory-file hosts.ini firstrun.yml -l <your_desktop_machine_hostname> --ask-pass --ask-become-pass

  and enter the password for your user on your desktop machine and another enter as the passwords will be the same.

## Install ROS2 to your raspberry pi:

- Run the following command:
  ansible-playbook --inventory-file hosts.ini ros2.yml -l <your_desktop_machine_hostname>

  This time everything should be automatically.

## Check installation

Afterwards check on your desktop machine with the follwoing commands:

  echo $ROS_DISTRO
  ros2

