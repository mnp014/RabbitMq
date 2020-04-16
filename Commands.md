#### Basic commands:
```
rabbitmqctl list_vhosts
rabbitmqctl list_queues -p <vhost>

rabbitmqctl cluster_status

rabbitmqctl stop_app
rabbitmqctl join_cluster <node>
rabbitmqctl start_app

rabbitmqctl report    # Dump detailed report on RabbitMQ instance  
```
---
#### Plugin management:
```
/usr/lib/rabbitmq/bin/rabbitmq-plugins enable <name>
/usr/lib/rabbitmq/bin/rabbitmq-plugins list   
```
---
#### Live modifications using eval:
```
rabbitmqctl eval 'application:set_env(rabbit, reverse_dns_lookups, true)
```
---
#### Configuring Limits:
 - Find out about actual limits
```
rabbitmqctl status | grep -A 4 file_descriptors
 {file_descriptors,
     [{total_limit,924},
      {total_used,831},
      {sockets_limit,829},
      {sockets_used,829}]},
```
 - To increase it to e.g. 10000 open files:
```
rabbitmqctl eval 'file_handle_cache:set_limit(10000).'
```
---
#### Managing RabbitMQ RAM Nodes:
NOTE: Can be used only in cluster with at least one disk node
Make the following entry to  `/etc/rabbitmq.conf` 
```
{cluster_nodes, {['[email protected]', '[email protected]', ...], ram}},
```
Or using CLI:
```
rabbitmqctl join_cluster --ram [email protected]
```
Note:  or if it is already in cluster
```
rabbitmqctl change_cluster_node_type ram
```
---
Miscellaneous:
 - Managment GUI on port 15627
 - RabbitMQ - Fix Chef 100% CPU usage
 - RabbitMQ - Setup Clustering

