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