# Ansible

```yaml
#Add ansible to Path
echo "export PATH=\"`python3 -m site --user-base`/bin:\$PATH\"" >> ~/.bashrc
source ~/.bashrc

#install boto3
pip3 install boto boto3
python3 -m pip3 install boto boto3

#install ansible-lint is with pip
python3 -m pip install --user ansible-lint

#install ansible module
sudo pip3 install pymysql
```

```yaml
#Concept
ansible_host=abc.com
ansible_connection=ssh/winrm/localhost
ansible_user=root/admin
ansible_ssh_pass/ansible_password=P@ssw0rd
```

```yaml
### Check services ###
- name : Check status ò a service and email if its down
  hosts: localhost
  tasks:
    - command: service httpd status
      register: result
    - mail:
        to: admin@commpany.com
        subject: Service alert
        body: Httpd Service is down
        when: result.stdout.find('down') != -1
```

```yaml
### Create users ###
- name : Create users
  hosts: localhost
  tasks:
    - user: name = "{{ item.name }}" state=present uid="{{ item.uid }}"
      loop:
        - name: joe # { name: joe, uid: 1010}
          uid: 1010
        - name: geogre # {name: geogre, uid: 1011}
          uid: 1011
```

```yaml
### Playbook run options ###
ansible-playbook playbook.yml --start-at-task "Start httpd service"
ansible-playbook playbook.yml --tags "install"
ansible-playbook playbook.yml --skip-tags "install"

ansible-config list #List all configuration
ansible-config view #Show the current config file
ansible-config dunp #Show the current settings
```
