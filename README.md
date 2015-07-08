Ridiculously simple example in which:

1. We use Vagrant to create a CentOS7 based VM from a previously imported box
2. Vagrant runs Ansible.  Ansible installs puppet and makes sure that a new
   manifest is inserted where it should be
3. Ansible then runs Puppet which creates a sample file.

The intent was to experiment with the following:

1. smdahlen\'s hostmanager plugin for vagrant
   https://github.com/smdahlen/vagrant-hostmanager
   
2. Provide a quick local way to experiment with the suggested
DigitalOcean [standalone puppet
examples|https://www.digitalocean.com/community/tutorials/how-to-install-puppet-in-standalone-mode-on-centos-7] experiments.

3. Investigate the interaction between vagrant\'s manipulation of ssh
   known\_keys and ansible\'s
   [inventory|http://docs.ansible.com/guide_vagrant.html] file and various name
   resolution services on the host.

