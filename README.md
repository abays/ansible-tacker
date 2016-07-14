# ansible-tacker

This Ansible playbook was quickly created to install Tacker on an overcloud controller node.  It was designed and tested against a node running RHEL 7.2 / OSP 8.  The current version assumes you have access to internal Red Hat repositories (that is, subscriptions will do you no good).

1. Make sure your overcloud node has an rc file available, and then set the appropriate group_var in the Ansible configuration.
2. This script assumes Neutron server is installed on the same node.
3. You will need to pass two extra parameters when running the playbook: tacker_admin_password and tacker_nova_password.  These are your admin and nova passwords, respectively.

In closing, I'm a total Ansible n00b.  This was my first attempt at learning it, so don't expect too much. ;-)
