# logstash-auditd
Logstash/grok filter for parsing auditd event logs and display it on the official module dashboard.
Elasticsearch docs seems to have example filters for all the other filebeat modules except this one. 

Made with Logstash 5.4, tested on CentOS 6. Might not work properly, feel free to contribute.


In order to get the events in /etc/audit/audit.rules we need to ensure that the following exists.

```
-a exit,always -F arch=b64 -S execve
-a exit,always -F arch=b32 -S execve
```

The filters are in the following order of record types processing groups
DAEMON_START
LOGIN
USER_LOGIN
EXECVE
SYSCALL
CRED_ACQ USER_CMD USER_START USER_ACCT USER_END
CWD PATH BPRM_FCAPS (pretty generic, probably will match everything else)

Enjoy!
