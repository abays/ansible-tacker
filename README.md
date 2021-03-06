# ansible-tacker

This Ansible playbook was quickly created to install Tacker on an overcloud controller node.  It was designed and tested against a node running RHEL 7.2 / OSP 8.  ***If you are not using Red Hat internal repos, make sure to pass "skip_repo_install=true" when running the playbook.*** *Please note that opting out of these repos will require you to properly configure the appropriate repos on the target host before running this playbook.*

1. Run this playbook from your undercloud.
2. Make sure your overcloud node has an rc file available, and then set the appropriate group_var in the Ansible configuration.
3. This script assumes Neutron server is installed on the same node.
4. You will need to pass two extra parameters when running the playbook: tacker_admin_password and tacker_nova_password.  These are your admin and nova passwords, respectively.  The playbook command would look something like so:
   ansible-playbook -i hosts site.yml -e tacker_admin_password=XXX -e tacker_nova_password=XXX
5. This script also assumes that your overcloud controller node is part of an HA cluster of size one (weird, eh?).  Certain services (such as neutron-server and httpd) should be managed by pacemaker and not systemd.  What I'm trying to say here is that this will probably only work with an overcloud that was deployed with a single controller.

In closing, I'm a total Ansible n00b.  This was my first attempt at learning it, so don't expect too much. ;-)
