Nagios check script for elasticsearch
=====================================

This is a simple script to check the status of an elasticsearch cluster.
It now supports elasticsearch 5.0 with or without x-pack authentication. 

Usage:

    ./check_elasticsearch -H es1.mysite.com -P 9200 -o /tmp [ -a ] [ -u <username> -p <password> ] 

This will output the standard Nagios format:

    OK - elasticsearch (elasticsearch) is running. status: green; timed_out: false; number_of_nodes: 1; number_of_data_nodes: 1; active_primary_shards: 2; active_shards: 2; relocating_shards: 0; initializing_shards: 0; unassigned_shards: 0 

`OK` / `WARNING` / `CRITICAL` correspond to the status being "green", "yellow", or "red" respectively.

Enjoy.

# Nagios3 snippets 

Adding something like this might help with Nagios3 config :

```
define command {
    command_name check_elasticsearch
    command_line /bin/bash /etc/nagios3/check_elasticsearch -H '$HOSTADDRESS$'
}

define service {
    hostgroup_name elasticsearch-health
    hostgroup elasticsearch
    service_description ES_HEALTH
    check_command check_elasticsearch
    use generic-service
}

define host {
    host_name elasticsearch-a
    alias     elasticsearch-a
    address   192.168.0.1
    hostgroups elasticsearch
}
define host {
    host_name elasticsearch-b
    alias     elasticsearch-b
    address   192.168.0.2
    hostgroups elasticsearch
}
```

# License

MIT.

