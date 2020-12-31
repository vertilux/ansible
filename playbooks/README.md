# Playbook's Collection

This is a collection of playbooks.

### Logrotate
Configuring Logrotate For Rails Production Logs.
Running `ansible-playbook append-logrotate.yml --extra-vars "env=ENV" -K -i inventory.yml` will edit `sudo vim /etc/logrotate.conf`, and at the bottom of the file the following block of code (change the ENV, ex: accltd):   

```
/home/deploy/erp-ENV/current/log/*.log {
  daily
  missingok
  rotate 7
  compress
  delaycompress
  notifempty
  copytruncate
}
```

**How it works:**   
- daily – Rotate the log files each day.
- missingok – If the log file doesn’t exist, ignore it.
- rotate 7 – Only keep 7 days of logs.
- compress – GZip the log file on rotation.
- delaycompress – Rotate the file one day, then compress it the next day so we can be sure that it won’t interfere with the Rails server.
- notifempty – Don’t rotate the file if the logs are empty.
- copytruncate – Copy the log file and then empties it.

**Running Logrotate:**   
Then the playbook will run: `sudo /usr/sbin/logrotate -f /etc/logrotate.conf`

