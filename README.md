Vagrant Ansible Project 
=======================
This git repository is to quickly set up a Vagrant proejct.
The Vagrantfile uses ansible software installed on the host machine
to initialize the virtual machines.  

If your host machine doesn't have, or can't run, ansible 
this isn't the project for you.

Setup
-----
- Edit the machine_define.yml file to match your desired machine characteristics
- Add roles to the roles/directory
- Update provision.yml to execute desired roles
- Edit Vagrantfile: Set config.vbguest.auto_update to false if you don't want to 
  update the Virtualbox Guest Additions installation.  Comment out if you are 
  using a different hypervisor, or the vagrant-vbguest plugin isn't installed.

License
-------
MIT

Author
------
Glenn H. Snead
