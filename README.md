IAC Nextcloud Installation
=========

This repository hosts an Infrastructure-as-Code (IAC) project that deploys a Nextcloud server using Ansible. Nextcloud is an open-source, self-hosted file share and collaboration platform. It's a safe home for all your data, and it gives you access to your files wherever you are and allows you to share them with others.

Requirements
------------

1. A server or virtual machine to host Nextcloud, preferably running a Linux distribution such as CentOS or Ubuntu.
1. Ansible installed on your control node (your local machine or wherever you choose to run your playbooks from). You can learn how to install Ansible here.
1. SSH access from your control node to your Nextcloud server.

Setup
-----

### Clone the repository

On your control node, clone the repository with the following command:

```
git clone https://github.com/JelleFirlefyn/IAC-Nextcloud-Ansible.git
```

### Configure your inventory

Modify the host file to include the IP addresses/DNS names of your hosts. For example:

```
[nextcloud]
server1.example.com
```

### Configure your variables

Edit the variable files in `nextcloud/vars/` according to your requirements. For instance, you might need to change the version of Nextcloud to install, or specify the necessary PHP version. Make sure to read the comments above each variable to understand their purpose.

### Run the playbook

From the root of the cloned repository, run the following command:

```
ansible-playbook main.yml
```

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).

# IAC-Nextcloud-Ansible
installation source: https://linux.how2shout.com/how-to-install-nextcloud-on-almalinux-9-rocky-linux-9/

Setup role for certificates:
`ansible-galaxy install geerlingguy.certbot`

