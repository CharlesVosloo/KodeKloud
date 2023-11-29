# KodeKloud 

Hello 🖐️ my name is Charles Vosloo.<br>  This is part of my <span style="color: red;">*journey*</span> learning DevOps while doing [KodeKloud Engineer](https://engineer.kodekloud.com/) challenges.
## Table of Contents
1. [Easy One Command to SSH to Nautilus Servers](##1.-Easy-One-Command-to-SSH-to-Nautilus-Servers)
1. [Using Ansible to do Linux tasks](##2.-Using-Ansible-to-do-Linux-tasks)
1. [Scripts](##3.-Scripts)
   


   


## 1. Easy One Command to SSH to Nautilus Servers
| Server         |      User                 |  SSH                             |
|--------------------------|--------------------------|:-----------------------------------------------------------------------------|
| Stratos App 1            |  tony@stapp01            |  `sshpass -p Ir0nM@n ssh -o StrictHostKeyChecking=no tony@172.16.238.10`      |
| Stratos App 2            |  steve@stapp02           |  `sshpass -p Am3ric@ ssh -o StrictHostKeyChecking=no steve@172.16.238.11`     |
| Stratos App 3            |  banner@stapp03          |  `sshpass -p BigGr33n ssh -o StrictHostKeyChecking=no banner@172.16.238.12`   |
| Stratos Load Balancer    |  loki@stlb01             |  `sshpass -p Mischi3f ssh -o StrictHostKeyChecking=no loki@172.16.238.14`     |
| Stratos Database Server  |  peter@stdb01            |  `sshpass -p 'Sp!dy' ssh -o StrictHostKeyChecking=no peter@172.16.239.10`     |
| Stratos Storage Server   |  natasha@ststor01        |  `sshpass -p Bl@kW ssh -o StrictHostKeyChecking=no natasha@172.16.238.15`     |
| Stratos Backup Server    |  clint@stbkp01           |  `sshpass -p H@wk3y3 ssh -o StrictHostKeyChecking=no clint@172.16.238.16`     |
| Stratos Mail Server      |  groot@stmail01          |  `sshpass -p Gr00T123 ssh -o StrictHostKeyChecking=no groot@172.16.238.17`    |
| Jenkins Server           |  jenkins@jenkins         |  `sshpass -p 'j@rv!s' ssh -o StrictHostKeyChecking=no jenkins@172.16.238.19`  |

## 2. Using Ansible to do Linux tasks

The best way to learn ansible is to use for all server configuration tasks as it was intended for. Many of the Linux KodeKloud Engineer questions can be done using ansible. I first leaned this from [Anh Nguyen](https://github.com/ntheanh201/kodekloud-engineer), where he provides solutions to KodeKloud Engineer linux challenges using ansible. So, instead here, I am going to provide my methodology here with an example. After installing and setting up ansible on jump host, a chatGPT prompt can help produce a sample playbook that might only need some tweaking :-).

1. The first step is to clone this repo on Jump Server 
```
git clone https://github.com/journeyman33/kodekloud.git
```
2. Then copy these lines Run to install the ansible install script on jump host. 
```
cd /home/thor/kodekloud 
sudo -s 
./scripts/install_ansible.sh  
```
 The ansible install script listed below will copy ansible.cfg and ansible inventory hosts file from the repo to the default /etc/ansible/ location on jump host which means that ansible can be run from anywhere 

```
#!/bin/bash
yum install epel-next-release -y
yum install ansible -y
cp /home/thor/kodekloud/ansible.cfg /etc/ansible/ansible.cfg
cp /home/thor/kodekloud/inventory/hosts /etc/ansible/hosts
```

Below is a table summarizing the usage of the ansible ping ad hoc command, which  will now work on all Nuatilus Severs:  

 Nautilus Server(s)            | Ansible ad hoc command            | alias
|----------------------------|-----------------------------------|---------------|
| stapp01, stapp02, stapp03  |  ansible webservers -m ping       | webservers
| Stratos App 1              |  ansible stapp01 -m ping          | stapp01                                         |
| Stratos App 2              |  ansible stapp02 -m ping          | stapp02                                          |
| Stratos App 3              |  ansible atapp03 -m ping          | stapp03
| Stratos Load Balancer      |  ansible loadbalancer -m ping     | loadbalancer 
| Stratos Database Server    |  ansible database -m ping         | storage
| Stratos Backup Server      |  ansible backup -m ping           | backup
| Stratos Mail Server        |  ansible mail -m ping             | mail



3. Now, let's write a playbook!



## 3. Scripts




