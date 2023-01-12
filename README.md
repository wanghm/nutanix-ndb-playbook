# nutanix-ndb-playbook

Ansible playbook to create postgres HA golden image for Nutanix NDB

## Directory Structure

```
.
├── LICENSE
├── README.md
├── ansible.cfg
├── group_vars
│   └── all
│       ├── private.yml
│       └── public.yml
├── host_vars
├── inventory
├── ndb-playbook.yml
└── roles
    └── postgres_ha
        ├── defaults
        ├── files
        ├── handlers
        ├── tasks
        │   ├── centos_7.yml
        │   └── main.yml
        └── templates
```

## Prepare private.yml
```
ansible_connection: ssh 
ansible_ssh_user: xxxxxxxx
ansible_ssh_pass: "xxxxxxxxxx"
```
You can encrypt it by ansible-vault:

```ansible-vault encrypt group_vars/private.yml```


## Run playbook

``` ansible-playbook -i inventory ndb-playbook.yml```

or

``` ansible-playbook -i inventory ndb-playbook.yml --ask-vault-pass```