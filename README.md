# Ansible + Openresty + Redis on Centos7
This repository stores ansible playbook for installing Openresty (Nginx+lua) on Centos 7. 
It also installs Redis database into the host.

# How it works
Once installed, user is able to visit the specific page to store it's user-agent key into Redis database. Once the key is stored, every other visit with the same user-agent increments it's value by one.

# Default configured links

*Visiting this link, you will store your user-agent into the database*
- 127.0.0.1/set

*Visiting this link, you will be able to query the database with the key specified.*
- 127.0.0.1/get?key=**YOURVALUE**

# Installation

This playbook was created using Ansible 2.8.1.

To launch the playbook, from the root directory, launch like this:
ansible-playbook -i hosts playbooks/launch_hw.yml

# Example usage

This is an example of usage using curl. Let's say we want to manipulate our user-agent header, providing a custom value to the server.


*To set the key in the database:*

**curl -H "User-Agent: Baravykas" 127.0.0.1/set**

*To query a specified value:*

**curl 127.0.0.1/get?key=Baravykas**
