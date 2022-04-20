- Device: FortiWifi 60E
- OS Version: v7.0.3
- Unlicensed/No Support Agreement

You'll want to start by navigating to your admin web interface and enabling certificates from System > Feature Visibility

I'm not going into much detail on how to install Ansible or configure a playbook. I will, however, attempt to provide links to the necessary resources.

- [Install Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#installing-ansible-on-ubuntu)
- [Install Ansible Galaxy Collections](https://docs.ansible.com/ansible/latest/galaxy/user_guide.html#the-command-line-tool)
- [Install FortiOS Ansible Galaxy](https://ansible-galaxy-fortios-docs.readthedocs.io/en/latest/install.html#install-fortios-ansible-galaxy)
    

I configured my host inventory and playbook structure similar to the ones in the [official FortiOS Ansible playbook documentation](https://ansible-galaxy-fortios-docs.readthedocs.io/en/latest/playbook.html#run-your-first-playbook), and used the "fortios\_access\_token" method in my inventory file.

In my own setup, I am currently using my existing [Secure Web Application Gateway (SWAG)](https://github.com/linuxserver/docker-swag) instance that has Certbot bundled in. It's a great Nginx reverse-proxy, certificate manager, etc. all-in-one solution. Currently my process is to just use Ansible to rsync the generated certs from the Docker mounted SWAG volume to a local folder in my Ansible host, and send them up to the Fortigate or other services/devices from there. You can also use [Ansible to generate your certs](https://graspingtech.com/ansible-lets-encrypt-esxi/), or [Certbot standalone](https://certbot.eff.org/instructions), or just pull them in from wherever if you have them stored locally anywhere ansible can reach. 

There is some additonal info in this Github issue that explains why the module used is different from that of the Ansible Galaxy documentation 

https://github.com/fortinet-ansible-dev/ansible-galaxy-fortios-collection/issues/78#issuecomment-817255184 
