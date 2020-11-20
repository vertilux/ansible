Logrotate
=========

Configuring Logrotate For Rails Production Logs.   
This role edit `/etc/logrotate.conf`, at the bottom of the file an add the following config block:

```
/home/deploy/APPNAME/current/log/*.log {
  daily
  missingok
  rotate 7
  compress
  delaycompress
  notifempty
  copytruncate
}
```

How it works:
-------------

- daily – Rotate the log files each day.
- missingok – If the log file doesn’t exist, ignore it.
- rotate 7 – Only keep 7 days of logs.
- compress – GZip the log file on rotation.
- delaycompress – Rotate the file one day, then compress it the next day so we can be sure that it won’t interfere with the Rails server.
- notifempty – Don’t rotate the file if the logs are empty.
- copytruncate – Copy the log file and then empties it.

Role Variables
--------------

In order to properly run this role make sure the variables env and user where set at prompt when the entry point playbook was executed.

Example Playbook
----------------

This role is not public on the Ansible's Galaxy community, it works only for Vertilux scenario.

Author Information
------------------

Jose Perez (a.k.a LePepe)
