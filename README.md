# ansible-playbooks
Automation of boring tasks!!!

###Clone the repo locally
```shell
git clone https://github.com/scurtyhub/ansible-playbooks.git
```

###Create SSH Keys
```shell
ssh-keygen -t ed25519 -C "ansilbe"
Copy the contents of "~/.ssh/ansible" to "key" value in "initial-setup/tasks/main.yaml"

cd ansible-playbooks
vi hosts
```
###Update hosts file with list of hosts
```shell
#Sample hosts file
#The file has all the list of k8s workers and nodes ip addresses/DNS names.

#k8s-master
[master]
192.168.40.159

#k8s worker nodes
[workers]
192.168.60.169
192.168.20.169
192.168.40.149
192.168.30.169
```

##Ansible-playbooks
###Adding Ansilbe user, SSH keys to remote hosts and adding the user's sudoers file.

```shell
#Run initial-setup task to setup "ansible" user on remote hosts

ansible-playbook --user <username> --ask-pass -K site.yml --tags "ansible-user"
ansible-playbook --user ubuntu --ask-pass -K site.yml --tags "ansible-user"
```

###Update, Upgrade and Rebooting remote hosts
```shell
ansible-playbook site.yml --skip-tags "ansible-user"
```