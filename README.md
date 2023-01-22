# software-setup

## Setup:

- Edit hosts.ini:
  - Replace <your_raspberrypi_fqdn> with the full qualified domain name of your freshly installed raspberry pi
  - Replace <your_desktop_hostname> with the hostname of your desktop machine
  - Replace <your_desktop_fqdn> with the full qualified domain name of your desktop machine
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
