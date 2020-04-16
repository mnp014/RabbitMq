```
rabbitmqctl list_vhosts
rabbitmqctl list_queues -p <vhost>

rabbitmqctl cluster_status

rabbitmqctl stop_app
rabbitmqctl join_cluster <node>
rabbitmqctl start_app

rabbitmqctl report    # Dump detailed report on RabbitMQ instance  
```
#### Plugin management:
```
/usr/lib/rabbitmq/bin/rabbitmq-plugins enable <name>
/usr/lib/rabbitmq/bin/rabbitmq-plugins list   
```
#### Live modifications using eval:
```
rabbitmqctl eval 'application:set_env(rabbit, reverse_dns_lookups, true)
```
