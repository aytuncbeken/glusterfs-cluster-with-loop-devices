# GlusterFS Replicaion on Loop Devices with Ansible
When it comes to create GlusterFS Replication, it can be hard and time consuming. Also adding loop devices to this picture makes things harder.<br>
For that reason, I created Ansible playbook which creates and configure GlusterFS on Loop devices with basic configuration.

## What does it do ? 
This Ansible playbook,
- Install necessary packages
- Create image files with size defined in playbook
- Create loop devices with image files
- Create mount directories
- Create GlusterFW Replication
- Mount 

## Requirements
For able to use this Playbook,
- Your servers/hosts should be Ansible ready
- Ansible user should be able to **[become](https://docs.ansible.com/ansible/latest/user_guide/become.html#id1)**
- Servers/hosts can communicate each other. (For FW restrictions look at [this](https://docs.gluster.org/en/v3/Administrator%20Guide/Setting%20Up%20Clients/))

## Usage
For create GlusterFS Replication,
- Define your servers/hosts in the ```hosts``` file under ```glusterfs_servers``` group
- Define the size of the disk in ```install.yml``` file which will be created as loop device
- Run playbook with the command below
```
ansible-playbook -i hosts install.yml
```
After successful install, directory ```/my-gluster-disk``` will be mounted on all servers/hosts. This directory is the GlusterFS Replicated directory. You can user this path to store your files and folders.

## Uninstall
For removing GlusterFS Replication run the command below
```
ansible-playbook -i hosts uninstall.yml
```

## Advanced configuration
For advanced configuration, you can change the file ```roles/gluster-loop-cluster/defaults/main.yml``` for your needs.
