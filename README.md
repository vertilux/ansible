# Inventory

#### Location   
`/etc/ansible/hosts`   

#### Structure   
```yml
[app]
127.10.15.1
127.10.15.2
127.10.15.3

[db]
127.10.15.7
127.10.15.8

[multi:children]
app
db
```

# Commands

#### Check log files
`ansible production -b -a "ufw status" -u deploy -K`   

`-b, --become` run operations with become (does not imply password prompting)   
`-K, --ask-become-pass` ask for privilegue escalation password   

#### Run operations in the background
