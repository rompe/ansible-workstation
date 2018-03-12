# ansible-workstation
Ansible playbook to update freshly installed Linux workstations for my needs

## Usage

For the default installation:
```
ansible-pull -U https://github.com/rompe/ansible-workstation
```

In addition, for NFS servers:
```
ansible-pull -U https://github.com/rompe/ansible-workstation nfs-server.yml
```

The host name `localhost` is used per default. This only works if /etc/ansible/hosts ist left
empty or features a `localhost` line.

## Disclaimer

If you aren't me, you probably don't want to use this.
