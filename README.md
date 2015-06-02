### Test Fedora 22 on the Rackspace Cloud

This small ansible playbook will take a Fedora 21 instance on Rackspace Cloud and upgrade it to Fedora 22.  It takes 7-9 minutes to run in most cases (sometimes less).

##### Getting started
Ensure that you [have ansible installed](http://docs.ansible.com/intro_installation.html) on your system.  (That's outside the scope of these instructions.)

1. Build a Cloud Server (a small 1GB server works fine).
2. Replace `example.com` in hosts.yml with your Cloud Server's IP address.
3. Run the playbook: `ansible-playbook -i hosts.yml playbook.yml`

##### Behind the scenes
The playbook automates these tasks for you:

1. Install prerequisites in Fedora 21 and update all packages
2. Switch bootloaders from extlinux to grub2
3. Download Fedora 21 upgrade packages and then install them (long step)
4. Reboots and relabels SELinux contexts during reboot (long step)
5. Waits for server to come back and verifies that Fedora 22 is installed

**PLEASE DON'T USE THIS ON A PRODUCTION SYSTEM YOU CARE ABOUT!**  You need to test your applications and configurations to ensure they will work properly on a system running Fedora 22.

Enjoy!  _-- Major_
