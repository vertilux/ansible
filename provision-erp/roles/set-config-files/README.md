Set Configuration Files
=========

This role copy the main ERP configuration files from Headquarters create the new directory, rename the environment and sql server port. 

Role Variables
--------------

Make sure `env`, `user` and `port` variables are set at prompt when entry point playbook is executed.   
`port` is not the SQL server, it is set on the firewall.

Example Playbook
----------------

This role is not public on the Ansible's Galaxy community, it works only for Vertilux scenario.

TODOs
------------------

 - Set template to avoid copying files from an existing application.

Author Information
------------------

Jose Perez (a.k.a LePepe)
