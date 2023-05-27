### Setup ansible
1. Create Directory my_ansible
`mkdir my_ansible` 
2. Create python enviroment
`pyenv virtualenv 3.10 my_ansible'
3. Activate enviroment 
`pyenv shell my_ansible'
4. Install ansible
`pip install ansible`
5. Create folder ansible and cd to that folder
`mkdir ansible` & `cd ansible`
6. create ansible.cfg hosts.yaml
7. Add host server to hosts.yaml file
```
[ours]
ansibling ansible_host=178.128.211.247
ansibling2 ansible_host=143.198.94.42
```
8. Create Invetory
```
[defaults]
inventory = hosts.yaml
remote_user = root
```
9. Connect to hosting server from dev enviroment
```
ansible ansibling -a "ls -l /" -v
```
10. Create Playbook for Install app and pkg on server hosting
```
mkdir playbook_test.yaml
```
11. add playbook install 
```
---
- name: Test playbook
  hosts: ours

  tasks:
  - name: Install NGINX
    ansible.builtin.apt:
      name: nginx
  - name: Install postgresql
    ansible.builtin.apt:
      update_cache: true
      pkg:
        - postgresql
```
12. Run install from your Dev enviroment
```
ansible-playbook playbook_test.yaml -f 2
```



