---
Title: Anacron 
Description: 
Date: 17-02-2021
Tags: #cron, #linux
References: 
Editor: markdown
---

# Anacron
Job scheduler that works async. It can be used to control the execution of daily, weekly and monthly jobs for systems that don't run 24 hours a day.

In cron if a machine is not running on time of a scheduled job then it will skip it, anacron is different it first checks for timestamp of the job of the job then decides whether to run it or not and if its timestamp is >=n(n is defined number of days) then runs it after a specified time delay. 


### File
`/etc/anacrontab` to add jobs
```bash
#contains the jobs based on timestamp.
/var/spool/anacron 

#eg
/var/spool/anacron/cron.daily
/var/spool/anacron/cron.weekly
/var/spool/anacron/cron.monthly
```

Obsidian references: [[cronie]]