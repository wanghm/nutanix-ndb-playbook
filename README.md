# nutanix-ndb-playbook

Ansible playbook to create postgres HA golden image(template VM) for Nutanix NDB

## Directory Structure

```
.
├── LICENSE
├── README.md
├── ansible.cfg
├── group_vars
│   └── all
│       ├── private.yml # private variables (credential)
│       └── public.yml  # variables
├── host_vars
├── inventory    # host IPs
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

## Prepare group_vars/public.yml

```
postgressql_src_url: https://ftp.postgresql.org/pub/source/v14.6/postgresql-14.6.tar.gz
postgressql_src_ver: postgresql-14.6
src_dir: /usr/local/src
postgres_dir: /usr/pgsql-14/
```


## Prepare group_vars/private.yml
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