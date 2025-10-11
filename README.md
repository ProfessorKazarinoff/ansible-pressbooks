# ansible-pressbooks

A repo of ansible playbooks for deploying a Pressbooks instance on a Digital Ocean VPS. Tested on a Digital Ocean VM with 2GB of memory running Ubuntu 22.04 LTS

## Steps

Initial Server Setup - apt update, new user, pressbooks user

MySQL Setup

Wordpress Setup

Nginx Setup

Certbot Setup

Pressbooks Setup

## Tutorial

Create vm. Digital Ocean is used for testing.

copy inventory-example file and save as inventory

```cp inventory-example.ini inventory.ini```

in inventory file: rename server group in brakets and write serve IP address below server group name

try and ping the server using the root user

 ```ansible -i inventory.ini hosts -m ping -u root```

copy ansible-example.cfg and save as ansible.cfg.

```cp ansible-example.cfg ansible.cfg```

In ansible.cfg specify, inventory file.

try and ping the server using the root user

```ansible hosts -m ping -u root```

try to run an ansible ad hoc command

```ansible hosts -a "free -h" -u root``` and 
```ansible hosts -a "date" -u root```


These use the default ```-m command``` module and sets ```-a "argument"``` sent to that module. so ```ansible hosts -m command -a "date" -u root``` is the same as the previous command.

copy vars/default-example.yml as vars/default.yml.

```cp vars/default-example.yml vars/default.yml```

Edit vars/default.yml with the usernames, versions and apt packages you want to install

Look at prod.yml and comment out the roles/playbooks you don't want to run. An option is to just start with the ```common``` role, which just sets up the server with a new user and install apt packages.

try and run the initial server setup playbook

```ansible-playbook prod.yml -u root```

After that you can try running it as your new user

```ansible-playbook prod.yml -u <user_name from vars/default.yml>```

Comment and uncomment out roles in prod.yml to proceed with the installation.
