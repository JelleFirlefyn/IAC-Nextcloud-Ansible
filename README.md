IAC Nextcloud Installation
=========

This repository hosts an Infrastructure-as-Code (IAC) project that deploys a Nextcloud server using Ansible. Nextcloud is an open-source, self-hosted file share and collaboration platform. It's a safe home for all your data, and it gives you access to your files wherever you are and allows you to share them with others.

Requirements
------------

1. A server or virtual machine to host Nextcloud, preferably running a Linux distribution such as CentOS or Ubuntu.
1. Ansible installed on your control node (your local machine or wherever you choose to run your playbooks from). You can learn how to install Ansible [here](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html).
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

### Install certificate role

Install the certificate role used:

```
ansible-galaxy install geerlingguy.certbot
```

### Certificates

Change the `main.yml` file in the root directory of this repository so it uses the right domain and email for creating the certificates

```
# Replace this domain with your actual domain you want to use
# In the case of multiple domains remove the '#' from the second line beneath this line
          - "cloud.example.com"
#         - "other.example.com"
# Replace this email address with the administrator email address linked to the domain
        email: "admin@example.com"
``` 

In case you do not want to create certificates remove the last line of code inside this file

```
# Remove the following line to prevent the creation of certificates:
    - geerlingguy.certbot
```

### Run the playbook

From the root of the cloned repository, run the following command:

```
ansible-playbook main.yml
```

### Configure Nextcloud to your preferences

Go to the web interface of Nextcloud via the DNS or IP of the machine where the installation took place and configure Nextcloud.

What the playbook does
----------------------

The playbook executes a series of tasks on your specified hosts to prepare them for the Nextcloud installation, including:

1. Updates the OS.
1. Installing necessary packages and dependencies.
1. Disabling SELinux until the next reboot and firewall rules as necessary.
1. Configuring Apache and its modules.
1. Configuring the MySQL database and creating necessary databases and users for Nextcloud.
1. Configuring PHP and its modules.
1. Downloading and extracting the specified version of Nextcloud.
1. Configuring the web server.

After the playbook is successfully run, you should be able to access your Nextcloud instance by navigating to your server's IP address or domain name in a web browser.

Dependencies
------------

`ansible-galaxy install geerlingguy.certbot`

Source
------

[Source used for manual installation and configuration of Nextloud](https://linux.how2shout.com/how-to-install-nextcloud-on-almalinux-9-rocky-linux-9/)

Author Information
------------------

JelleFirlefyn
