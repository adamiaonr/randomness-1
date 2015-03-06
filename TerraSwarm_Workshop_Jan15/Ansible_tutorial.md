# Another Ansible Tutorial
*by Adwait Dongare*

(This is a very fresh tutorial. Please forgive any errors and misconceptions.)

* What is Ansible?
	- Configuration management tool like chef or puppet. Let's you manage a lot of machines from a single "script" called a playbook. It uses various modules (generally written in python) for various tasks.
	- The project is here: [http://www.ansible.com/home](http://www.ansible.com/home)
	- We will use it to push changes/tasks to a large number of swarmboxes at once. It plays nicely with docker.

* Why Ansible?
	- Works better with docker (which is a container manager you would probably be using)
	- Does not need a client service as everything happens over ssh
	- Only needs to be installed on the orchestration machine
	- We considered OpenStack, Chef, Puppet etc for orchestration. They did not seem to provide the required integration and simplicity.

* What do you need for this tutorial?
	1. Orchestration machine (a laptop with linux, installed or as VM, would do). Now onwards, call this 'host'.
	2. Internet connection (without proxies etc for simplicity)
	3. Deployment machine with a fresh minimal ubuntu install (may also be a VM, but make sure you can ssh into it shortcut: used a bridged network). Now onwards, call this 'target'.
	4. ssh access from the host machine to the target machine.
	5. For simplicity, we will have them on the same physical network. If on different networks, you need to setup appropriate forwarding etc. (Same stuff you need to do to be able to ssh into the machines)

* Resources:
	- Ansible documentation: [http://docs.ansible.com/](http://docs.ansible.com/)
	- Ansible github repo: [https://github.com/ansible/ansible](https://github.com/ansible/ansible)
	- Ansible examples github repo: [https://github.com/ansible/ansible-examples](https://github.com/ansible/ansible-examples)

* The Installation Tutorial
	1. Installation on the host machine
Example with Debian Wheezy host machine (others work equally well). Using the pip method.
```
sudo apt-get install python-pip python-dev
```
other possible dependencies: paramiko, PyYAML, jinja2
pip install PyYAML jinja2 paramiko
```
sudo pip install ansible
```
	2. Host file on host machine
Ansible uses the 'hosts' file at `/etc/ansible/hosts`
A sample hosts file can be found in `./ansible/` examples
Create a set of webservers (named eg NUC) with the address or hostname of your NUC/VM

	3. Set up ssh keys with target machines on the network
Tutorial if you haven't done this before: [https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys--2](https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys--2)

generate keypair on host:
```
ssh-keygen -t rsa
```
This creates `id_rsa` (private key) & `id_rsa.pub` (public key) in `~/.ssh`

add public key to target server:
```
ssh-copy-id -i ~/.ssh/id_rsa.pub user@123.45.67.89
```
add private key to identity:
```
ssh-add ~/.ssh/id_rsa  
reboot
```

* Ansible Usage Tutorial
-Step 4. Ad-Hoc Commands in Ansible
If the hosts file and ansible installation are all correctly done, we should be able to ping the host from the target (note the reversal)

ansible all -m ping
all: do action on all targets
-m: module flag
ping: name of module

other eg. uses:
ansible all -m ping -u bruce

refer to http://docs.ansible.com/intro_getting_started.html for other examples

running commands in Ad-hoc mode:
ansible all -a "/bin/echo hello"

say we want to only do these actions 10 at a time:
ansible NUC -a "/sbin/reboot" -f 10

Ad-hoc mode guide:
http://docs.ansible.com/intro_adhoc.html

-Step 5. Using Playbooks
Playbooks are like scripts.Playboks are written using the YAML syntax. A guide can be found here:
http://docs.ansible.com/YAMLSyntax.html

The playbooks tutorial:
http://docs.ansible.com/playbooks_intro.html

hosts: which machines to target
vars: variable names
remote_user: which user to use on the target
sudo: (yes/no) whether to run as sudo
name: just the name of the task. Not really used for processing but used for output

the general syntax:
module: parameter1=value1 parameter2=value2 ...

save as filename.yml

execute with:
ansible-playbook filename.yml
use -K flag if using as sudo. if you use sudo=yes but dont provide -K or don't have the required ssh keys for sudo users setup, the play will get stuck and result in an error after some time.

exercise application using playbooks with immediate gratifying results:
1. reboot all machines (shutdown -r now)
2. display a message on the terminal screen of all machines (use wall)
3. check connection between host & target (use the ping module)
4. install cowsay fortune on targets and see if you can get $fortune | cowsay to work

To use playbooks, you need to have the required modules. Ansible has a lot of useful built-in modules eg. command, git, ssh, ping, docker etc.

Some answers to questions you are likely to have:
- Can we use a playbook inside another playbook?
Yes. Use the include module. Syntax:
include: /bin/we/are/awesome.yml

* Other good tutorials & resources:
Rackspace tutorial which explains the complete process from installation to finish:
https://developer.rackspace.com/blog/move-fast-and-dont-break-things-testing-with-jenkins-ansible-and-docker/

About Ansible with Docker:
http://patg.net/ansible,docker/2014/06/18/ansible-docker/
