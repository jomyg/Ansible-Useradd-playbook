# Ansible playbook password encrytpted user creation

[![Build](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

---

## Description 

Simple ansible playbook for creating a user with password encrytpted on client node using Ansible Master node. 

----
## Pre-Requests
- Need to install Ansible on Master node to run
-----

### Ansible installation 

```sh
sudo amazon-linux-extras install ansible2 -y

ansible --version
ansible 2.9.23
  config file = /etc/ansible/ansible.cfg
  configured module search path = [u'/home/ec2-user/.ansible/plugins/modules', u'/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/lib/python2.7/site-packages/ansible
  executable location = /usr/bin/ansible
  python version = 2.7.18 (default, Jun 10 2021, 00:11:02) [GCC 7.3.1 20180712 (Red Hat 7.3.1-13)]
```


### Behind the code : hosts file
```sh
[amazon]                                                                                          >>>>  Group name i have provided
<server IP> ansible_user="ec2-user" ansible_port=22 ansible_ssh_private_key_file="ansible.pem"
```
### Behind the code : useradd.yml

```
---

- name: "USERADD SCRIPT"
  hosts: amazon
  become: true
  tasks:
   - name: "Creating an user now"
     user:
      name: admin
      uid: 2022
      password: "{{ 'password@123' | password_hash('sha512') }}"
      shell: /bin/bash
      createhome: yes
      home: /home/admin
      state: present
  ```
  

 ## Conclusion

Created the a user on clinet node with password encrypted using ansible playbook


#### ⚙️ Connect with Me

<p align="center">
<a href="mailto:jomyambattil@gmail.com"><img src="https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white"/></a>
<a href="https://www.linkedin.com/in/jomygeorge11"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white"/></a> 
<a href="https://www.instagram.com/therealjomy"><img src="https://img.shields.io/badge/Instagram-E4405F?style=for-the-badge&logo=instagram&logoColor=white"/></a><br />
