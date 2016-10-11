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

You have to install ansible and (for the Step 3 in the install instructions) sshpass

Install
-------

1. Install Archlinux Arm using this instructions

https://archlinuxarm.org/platforms/armv8/broadcom/raspberry-pi-3

2. Boot the raspberry pi and connect it to you network. Findout it's IP-Address
   set it in the hosts file (last line).

3. Prepare the raspberry pi with the following command:

ANSIBLE_HOST_KEY_CHECKING=False ansible-playbook -i hosts openslides_pi_init.yml

4. Open openslides_pi.yml and set the variables as you wish.

5. Then call

ansible-playbook -i hosts openslides_pi.yml

6. Connect a projector to the hdmi port of the raspberry pi and reboot it.
