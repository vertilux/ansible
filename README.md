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

#### Update servers asynchronously
`ansible multi -b -B 3600 -a "apt -y update` this command will return:   
```
127.10.15.1 | success >> {
    "ansible_job_id": "763350539037",
    "results_file: "/root/.ansible_async/763350539037",
    "started": 1
}
```
**Updating servers with Ansible**
`ansible production -m apt -a "upgrade=yes update_cache=yes" -u -b -K`   
Then I can reboot all servers with `ansible production -a "reboot" -s`.
