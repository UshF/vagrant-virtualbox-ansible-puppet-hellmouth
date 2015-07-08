Ridiculously simple example in which:

1. We use Vagrant to create a CentOS7 based VM from a previously imported box
2. Vagrant runs Ansible.  Ansible installs puppet and makes sure that a new
   manifest is inserted where it should be
3. Ansible then runs Puppet which creates a sample file.
