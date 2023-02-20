# Software Setup

Prepare and install a Raspberry Pi 4 which is freshly installed with Ubuntu 22.04 server with ROS2

## Install ros2 to your Raspberry Pi

### Setup:

- Run the following command:

  ```ansible-playbook --inventory-file hosts.ini config.yml```

  to configure the ansible setup with your usernames and IP addresses

### Prepare the Raspberry Pi for the ansible setup:

- Run the following command:
  
  ```ansible-playbook --inventory-file hosts.ini firstrun.yml -l pib --ask-pass --ask-become-pass```

  and enter the password for your user on the raspberry pi and another enter as the passwords will be the same.

### Install ROS2 to your raspberry pi:

- Run the following command:

  ```ansible-playbook --inventory-file hosts.ini ros2.yml -l pib```

  This time everything should be automatically.

### Check installation

Afterwards log into your raspberry pi and check with the following commands:

  ```echo $ROS_DISTRO```
  ```ros2```

## Install ros2 to your desktop system

If you want to install ROS2 to your desktop machine (actually Ubuntu 22.04 or Linux Mint Version 21.1):

### Prepare desktop machine for the ansible setup (if needed):

- Run the following command:

  ```ansible-playbook --inventory-file hosts.ini firstrun.yml -l desktop --ask-pass --ask-become-pass```

  and enter the password for your user on your desktop machine and another enter as the passwords will be the same.

### Install ROS2 to your desktop system:

- Run the following command:

  ```ansible-playbook --inventory-file hosts.ini ros2.yml -l desktop```

  This time everything should be automatically.

### Check installation

Afterwards check on your desktop machine with the follwoing commands:

  ```echo $ROS_DISTRO```
  ```ros2```

