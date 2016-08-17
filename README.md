# ansible-tacker

This Ansible playbook was quickly created to install Tacker on a node ***outside*** an overcloud's controller nodes.  Technically you could use this project to install Tacker on one of the controller nodes, but Tacker would not be HA-protected (unlike the other OpenStack services).  If you're looking for HA protection for Tacker, please use the "HA" branch of this project.  This project was designed and tested against nodes running RHEL 7.2 / OSP 8.  The current version assumes you have access to internal Red Hat repositories (that is, subscriptions will do you no good).

1. Run this playbook from your undercloud.
2. Make sure your overcloud controller nodes haave an rc file available, and then set the appropriate group_var in the Ansible configuration.
3. This script assumes Neutron server is installed on the controller nodes.
4. You will need to pass two extra parameters when running the playbook: tacker_admin_password and tacker_nova_password.  These are your admin and nova passwords, respectively.  The playbook command would look something like so:
   ansible-playbook -i hosts site.yml -e tacker_admin_password=XXX -e tacker_nova_password=XXX
5. Even though this is designed for HA-protected overcloud controller nodes, this script can still be used on a TripleO deployment containing only one controller.  Simply put that one host in the host's "[controller]" section.
6. The "[tacker-server]" section of the hosts file should contain the target host upon which to install Tacker.  Typically -- at least in a TripleO environment -- the "[database]" section of the host file should contain one and only one of the overcloud's controllers (assuming Galera is replicating the database across the cluster).

In closing, I'm a total Ansible n00b.  This was my first attempt at learning it, so don't expect too much. ;-)
