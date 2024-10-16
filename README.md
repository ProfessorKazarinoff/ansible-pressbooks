# ansible-pressbooks

A repo of ansible playbooks for deploying a Pressbooks instance on a Digital Ocean VPS.

## Steps

Initial Server Setup - apt update, new user, pressbooks user

MySQL Setup

Wordpress Setup

Nginx Setup

Certbot Setup

Pressbooks Setup

## Tutorial

copy inventory-example file and save as inventory

in inventory file: rename server group in brakets and write serve IP address below server group name

try and ping the server using the root user ```ansible -i inventory.ini hosts -m ping -u root```

copy ansible-example.cfg and save as ansible.cfg. In ansible.cfg specify inventory file.

try and ping the server using the root user ```ansible hosts -m ping -u root```

try to run an ansible ad hoc command ```ansible hosts -a "free -h" -u root``` and ```ansible hosts -a "date" -u root```
This uses the default ```-m command``` module and sets ```-a "argument"``` sent to that module. so ```ansible hosts -m command -a "date" -u root``` is the same as the previous command.

copy vars/default-example.yml as vars/default.yml. Edit vars/default.yml with the username and apt packages you want to install

try and run the initial server setup playbook

```ansible-playbook initial-server-setup.yml -u root```

After that you can try running it as your new user

```ansible-playbook initial-server-setup.yml -u <user_name from vars/default.yml>```

For wp role, see: https://github.com/sanjeebnepal/ansible-wordpress/blob/main/wordpress.yml
