# ansible-tacker

This Ansible playbook was quickly created to install Tacker on an overcloud's controller nodes.  It was designed and tested against nodes running RHEL 7.2 / OSP 8.  The current version assumes you have access to internal Red Hat repositories (that is, subscriptions will do you no good).

*** This branch is designed to support installing Tacker within an HA context ***

1. Run this playbook from your undercloud.
2. Make sure your overcloud controller nodes haave an rc file available, and then set the appropriate group_var in the Ansible configuration.
3. This script assumes Neutron server is installed on the controller nodes.
4. You will need to pass two extra parameters when running the playbook: tacker_admin_password and tacker_nova_password.  These are your admin and nova passwords, respectively.  The playbook command would look something like so:
   ansible-playbook -i hosts site.yml -e tacker_admin_password=XXX -e tacker_nova_password=XXX
5. Even though this is designed for HA, this script can still be used on a TripleO deployment containing only one controller.  Just leave the "controller-peer" hosts section empty.

In closing, I'm a total Ansible n00b.  This was my first attempt at learning it, so don't expect too much. ;-)
