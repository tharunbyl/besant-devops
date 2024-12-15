Configuration Managment Tool

master ansible 

Keybased auth
Keyless auth


1. Launch instance 
name
redhat 
4
pem
Auto assign Public ip

Setup Ansible

public master, private clients 

1) ad-hoc 
ansible <hosts!> -m ping

<all>
<ip>
<ip:ip..>
<group>
<group:group..>


ansible <hosts!> -m <module!> -a "name=<name!> state=<state!>" -b

-b or --become, to this command inside the client with super user privillage 

<state!>
installed   removed     latest
present     absent


ansible web yum -a "name=nginx state=installed" -b // sudo yum install nginx
ansible db -m copy -a "src=<src!> dest=<dest!>" // cp <src!> <dest!>
ansible all -m file -a "path=<path!> state=<touch!>"  //touch <path!>
ansible all -m file -a "path=<path!> state=directory"  //
ansible all -m shell -a "git --version"  // shell module is used to get client info
ansible all -m fetch -a "src=<client-path!> dest=<master-path!>"  // pull file from client to master src = /var/log/messages dest=.
ansible all -m fetch -a "src=<client-path!> dest=<master-path!> flat=yes"  //  src = /var/log/messages dest=./{{inventory_hostname}}_messages 
                                                                            // flat = yes, fetch without structure 


yum install tree // for directory struture 




2) playbook 



ansible-galaxy init nginx-role
nginx-role

tasks - copy, move, etc
files - static like index.html
tempalte - dynamic

defaults - overridden
vars - static

handlers

tests
    inventory
    test.yml