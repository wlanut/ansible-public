ssh-add-passphrase
=========

Uses provided variables to automatically add your desired ssh key (with passphrase) to an existing ssh agent. For more information, check out my blog post.

Requirements
------------

Expect package
> `sudo apt install expect`

https://linux.die.net/man/1/expect


Role Variables
--------------

- ssh_user: username **(for the expect script)**
- ssh_key_location: /home/username/.ssh/id_rsa **(path to privtae key)**
- ssh_passphrase: your_passphrase **(ssh passphrase)**

Dependencies
------------

None

Example Playbook
----------------

    - hosts: localhost
      roles:
         - roles/ssh-add-passphrase

License
-------

BSD

Author Information
------------------

blog.walnuthomelab.com

github.com/wlanut
