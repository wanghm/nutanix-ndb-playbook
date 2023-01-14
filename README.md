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
│       ├── private.yml  # private variables (credential)
│       └── public.yml   # variables
├── host_vars
├── inventory
├── ndb-playbook.yml
└── roles
    └── postgres_ha
        ├── files
        │   └── rhel8.repo
        ├── tasks
        │   ├── centos7.yml
        │   ├── main.yml
        │   └── rhel8.yml
        └── templates
```

## How to use this playbook
### 1. Prepare group_vars/public.yml

Configure postgressql_src_url, postgressql_src_ver, src_dir and postgres_dir

```
postgressql_src_url: https://ftp.postgresql.org/pub/source/v14.6/postgresql-14.6.tar.gz
postgressql_src_ver: postgresql-14.6
src_dir: /usr/local/src
pg_home: /usr/pgsql-14/
```

### 2. Prepare group_vars/private.yml (this file is not in the repository)
```
ansible_connection: ssh 
ansible_ssh_user: xxxxxxxx
ansible_ssh_pass: "xxxxxxxxxx"
era_user_password: "$1$wIxxxxxxxxxxxxxxxxxxxxxxxx/1"
postgres_user_password: "$2wIxxxxxxxxxxxxxxxxxxxxxxxxyy"

########
# get encrypt era_user_password and postgres_user_password by:
# openssl passwd -1 "mypassword"
# and set it in this file
```
You can encrypt this file by ansible-vault:

```ansible-vault encrypt group_vars/private.yml```


### 3.Run playbook

``` ansible-playbook -i inventory ndb-playbook.yml```

or (in case of using encrypt private.yml file)

``` ansible-playbook -i inventory ndb-playbook.yml --ask-vault-pass```