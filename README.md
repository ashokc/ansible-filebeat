# ansible-filebeat
[Ansible Galaxy](https://galaxy.ansible.com/ashokc/filebeat/)

Ansible role for Logstash. Tested platforms at this time are:

* Ubuntu 16.04

** Developed and Tested with Ansible version 2.4.1.0 **

##### Dependency
None.

This role has been used and tested with the [elastic.elasticsearch](https://github.com/elastic/ansible-elasticsearch) role as the provisioner for elasticsearch, [ashokc.kibana](https://github.com/ashokc/ansible-kibana) for Kibana, and [ashokc.filebeat](https://github.com/ashokc/ansible-filebeat) as part of an ELK stack.

## Usage

* Create your Ansible playbook with your own tasks
* Include the role ashokc.filebeat and override the role defaults

e.g. 

```
- hosts: filebeat-nodes
  become: true
  roles:
    - { role: ashokc.filebeat }
```

The following variables in defaults/main.yml can be overridden:

```
es_major_version: 5.x
elk_version: 5.6.1
es_apt_key: https://artifacts.elastic.co/GPG-KEY-elasticsearch
es_apt_url: deb https://artifacts.elastic.co/packages/{{ es_major_version }}/apt stable main
filebeat_user: filebeatUser
filebeat_group: filebeatGroup
filebeat_version: "{{ elk_version }}"
filebeat_enabled_on_boot: yes
filebeat_2_logstash_port: 5044
filebeat_logstash_hosts: localhost:{{filebeat_2_logstash_port}}
```

