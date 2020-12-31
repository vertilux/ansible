---
- hosts: all
  tasks:
    - name: Run ruby script to scrap LME/SMM
      command: /bin/bash -l -c  'cd /home/deploy/erp-accltd/scraper && ruby scraper.rb'
