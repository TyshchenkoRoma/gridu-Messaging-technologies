# gridu-Messaging-technologies

# run docker cotainers
# docker run -d --hostname rabbit1 --name rabbit1 -e RABBITMQ_ERLANG_COOKIE='rabbitcluster' -p 30000:5672 -p 30001:15672 rabbitmq:management
# docker run -d --hostname rabbit2 --name rabbit2 --link rabbit1:rabbit1 -e RABBITMQ_ERLANG_COOKIE='rabbitcluster' -p 30002:5672 -p 30003:15672 rabbitmq:management
# docker run -d --hostname rabbit3 --name rabbit3 --link rabbit1:rabbit1 --link rabbit2:rabbit2 -e RABBITMQ_ERLANG_COOKIE='rabbitcluster' -p 30004:5672 -p 30005:15672 rabbitmq:management

# join the cluster 1 
docker exec -i -t rabbit2 \bash
root@rabbit2:/# rabbitmqctl stop_app
Stopping node rabbit@rabbit2 ...
root@rabbit2:/# rabbitmqctl join_cluster rabbit@rabbit1
Clustering node rabbit@rabbit2 with rabbit@rabbit1 ...
root@rabbit2:/# rabbitmqctl start_app
Starting node rabbit@rabbit2 ...

# do the same for a second broker

# http://localhost:30001/#/ add port numbers
#