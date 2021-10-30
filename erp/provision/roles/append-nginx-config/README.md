Append Nginx Configuration File
=========

We use ansible blockinfile module, this module is used to insert/update/remove a block of lines in a file.
This module will insert/update/remove a block of multi-line text surrounded by customizable marker lines.   
In this role we append the main nginx configuration file with a new block.

Role Variables
--------------

In order to properly run this role make sure the variables `env` and `user` where set at prompt when the entry point playbook was executed.   

Example Playbook
----------------

This role is not public on the Ansible's Galaxy community, it works only for Vertilux scenario.

Author Information
------------------

Jose Perez (a.k.a LePepe)
