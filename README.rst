Ansible script to create an openslides box with an raspberry pi
===============================================================

This installs openslides on a raspberry pi 3. It also creates an open wlan on
whitch the openslides instance can be accessed. You can use any domain to access
openslides. When a projector is connected to the hdmi port of the rapberry pi,
then it shows the projector on it.


Requirements
------------

This is tested with a raspberry pi 3 but could also work with a raspberry pi 2
either with an wlan-stick or without the wlan option.

You have to install ansible and (for the Step 4 in the install instructions) sshpass

This script works either with Archlinux Arm or with Raspbian Stretch. To begin you have
to install one of this distributions.

Archlinux: https://archlinuxarm.org/platforms/armv8/broadcom/raspberry-pi-3

Raspbian: https://www.raspberrypi.org/documentation/installation/installing-images/README.md

Install
-------

1. Boot the raspberry pi and connect it to you network. Findout it's IP-Address
   set it in the hosts file (last line). 

2. Install ansible and sshpass with ``sudo apt-get install ansible sshpass``.

3. Make sure you have SSH keys in your roots home folder. You can create those on raspbian with

   ``sudo su``
   
   ``ssh-keygen``
   
   Agree to all questions of ssh-keygen. Raspbian also requires you to enable the SSH server in ``sudo raspi-config``.

4. Download the required ansible rolls:
   ``$ ansible-galaxy install -r requirements.yml``

5. Prepare the raspberry pi with the following command:

   For Archlinux:
   ``$ ansible-playbook -i hosts openslides_pi_init_archlinux.yml``

   For Raspbian:
   ``$ ansible-playbook -i hosts openslides_pi_init_raspbian.yml``

6. Open openslides_pi.yml and set the variables as you wish.

7. Then call
   ``$ ansible-playbook -i hosts openslides_pi.yml``

8. Connect a projector to the hdmi port of the raspberry pi and reboot it.
