Create Enable and Start Sidekiq Service
=========

We use Sidekiq as background job processing for our applications.   
Sidekiq uses threads to handle many jobs at the same time in the same process. It is integrated tightly with Rails to make background processing dead simple.   
This template role set the sidekiq service, enabled and start the service.

```
[Unit]
Description=sidekiq-{{env}}	
After=syslog.target network.target

[Service]
Type=simple
WorkingDirectory=/home/deploy/erp-{{env}}/current
ExecStart=/home/deploy/.rbenv/shims/bundle exec sidekiq -e {{env}}
User=deploy
Group=deploy
UMask=0002

# Greatly reduce Ruby memory fragmentation and heap usage
# https://www.mikeperham.com/2018/04/25/taming-rails-memory-bloat/
Environment=MALLOC_ARENA_MAX=2

# if we crash, restart
RestartSec=1
Restart=on-failure

# output goes to /var/log/syslog
StandardOutput=syslog
StandardError=syslog

# This will default to "bundler" if we don't specify it
SyslogIdentifier=sidekiq-{{env}}

[Install]
WantedBy=multi-user.target
```

Role Variables
--------------

In order to properly run this role make sure the variables env and user where set at prompt when the entry point playbook was executed.

Example Playbook
----------------

This role is not public on the Ansible's Galaxy community, it works only for Vertilux scenario.

Author Information
------------------

Jose Perez (a.k.a LePepe)
