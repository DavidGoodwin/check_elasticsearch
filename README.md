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

# License

MIT.

