Telegraf
========

An Ansible playbook to install, configure, and manage [Telegraf](https://github.com/influxdb/telegraf), the plugin-driven server agent for reporting metrics into InfluxDB.

Requirements
------------

Prior knowledge/experience with InfluxDB and Telegraf is highly recommended. Full documentation is available [here](https://docs.influxdata.com).

Role Variables
--------------

The high-level variables are stored in the `defaults/main.yml` file. The most important ones being:

```
# Channel of Telegraf to install (currently only 'stable' is supported)
telegraf_install_version: stable

#Influxdb Address
telegraf_influxdb_urls:
  - http://localhost:8086

#Influxdb credentials
telegraf_influxdb_username: telegraf
telegraf_influxdb_password: password
```

More advanced configuration options are stored in the `vars/main.yml` file, which includes all of the necessary bells and whistles to tweak your configuration.

Dependencies
------------

No other Ansible dependencies are required. This role was tested and developed with Ansible 1.9.4.

Execution
------------

For now, you need to be able to ssh into root account of each machine to do the instalation. this can be do by edditing ```/etc/ssh/sshd_config``` and add edit
```
FROM:
PermitRootLogin without-password
TO:
PermitRootLogin yes
```
This can be undo after instalation if needed.


for executing the playbook:
```
#Test Playbook & affected machines
ansible-playbook --list-hosts deploy-telegraf.yml

#Run Playbook
ansible-playbook test.yml -f 3 -k
```
