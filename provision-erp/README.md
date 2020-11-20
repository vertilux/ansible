# Provision ERP 

Provision ERP is a collection of ansibles roles created by Vertilux's IT to make easy 
the setup of multiples environments. Every environemnt is a distribution center, this 
approach makes us use the same code for all distribution centers and easy to maintain.

### Running playbooks

Make sure ansible is installed.   
`ansible-playbook entry_point.yml -i inventory.yml -k -K`   
Entry point is the "main" playbook, this is going to ask for:   

  - User name.
  - Environment (Sage300 SQL server name lowecase).
  - URL (DNS url for the application, Ex: erp.vertilux.com).
  - Port (SQL server port set on firewall rule).

### Roles 

- set-config-files
- append-nginx-config
- set-sidekiq-service
- logrotate

### TODO

- [ ] Set postgresql_db module role to add databases from a remote host.
