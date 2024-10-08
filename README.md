# apache-nifi-templates

## NiFi Cluster Configuration Steps (embedded Zookeper)
Step 1: Update the Host Entry

#Copy the same values to the other nodes

xx.xx.xx.xx nifi-node-1

xx.xx.xx.xx nifi-node-2

xx.xx.xx.xx  nifi-node-3



xx.xx.xx.xx - IP Addresses of the corresponding machines.



Step 2: Update zookeeper.properties (../nifi-1.8.0/conf/zookeeper.properties)

#Copy the same values to the other nodes

server.1=nifi-node-1:2888:3888

server.2=nifi-node-2:2888:3888

server.3=nifi-node-3:2888:3888



Step 3: Create "myid" file inside the Zookeeper Data Directory (../nifi-1.8.0/state/zookeeper/myid)

#Copy the same file to the other nodes and update the corresponding server id

Create myid file inside ./state/zookeeper and put the server id (1, 2, 3 respectively in each node)



Step 4: Update nifi.properties (../nifi-1.8.0/conf/nifi.properties)

#Copy the same values to the other node nodes and rename the corresponding node name

#nifi-node-1 to nifi-node-2 and nifi-node-3



#Enabling Embedded Zookeeper

nifi.state.management.embedded.zookeeper.start=true

#Connection String of Embedded Zookeepers

nifi.zookeeper.connect.string=nifi-node-1:2181,nifi-node-2:2181,nifi-node-3:2181



#Enabling Clustering

nifi.cluster.is.node=true

nifi.cluster.node.address=nifi-node-1

nifi.cluster.node.protocol.port=8081



#Setting the NiFi Node Name

nifi.web.http.host=nifi-node-1



#Site-to-Site protocol is used to distribute date between nodes in the cluster.

#Enabling Site-to-Site Protocol

nifi.remote.input.host=nifi-node-1

nifi.remote.input.socket.port=8082



#Property Used for Cluster Load Balancing (Only Available from NiFi 1.8.0+)

#Cluster Load Balancer will Redistribute Data from Failed NiFi Nodes

nifi.cluster.load.balance.host=nifi-node-1



#Property Used to Control the Starting of Cluster Election

nifi.cluster.flow.election.max.candidates=2



Step 5: Restart All NiFi Nodes



## NiFi Cluster Configuration Steps in Single Machine (Reference)
Create Copies of NiFi Binary in the same machine and follow the below steps.



Step 1: Update the Host Entry



#Point to localhost IP to all the node names

127.0.0.1 nifi-node-1

127.0.0.1 nifi-node-2

127.0.0.1 nifi-node-3



Step 2: Update zookeeper.properties (../nifi-1.8.0/conf/zookeeper.properties)



#NiFi Node 1 Properties

clientPort=2181

server.1=nifi-node-1:2888:3888

server.2=nifi-node-2:2889:3889

server.3=nifi-node-3:2890:3890



#NiFi Node 2 Properties

clientPort=2182

server.1=nifi-node-1:2888:3888

server.2=nifi-node-2:2889:3889

server.3=nifi-node-3:2890:3890



#NiFi Node 3 Properties

clientPort=2183

server.1=nifi-node-1:2888:3888

server.2=nifi-node-2:2889:3889

server.3=nifi-node-3:2890:3890



Step 3: Create "myid" file inside the Zookeeper Data Directory (../nifi-1.8.0/state/zookeeper/myid)



#Copy the same file to the other nifi nodes and update the corresponding server id

Create myid file inside ./state/zookeeper and put the server id (1, 2, 3 respectively in each instances)



Step 4: Update nifi.properties (../nifi-1.8.0/conf/nifi.properties)



#NiFi Node 1 Properties



#Enabling Embedded Zookeeper

nifi.state.management.embedded.zookeeper.start=true



#Connection String of Embedded Zookeepers

nifi.zookeeper.connect.string=nifi-node-1:2181,nifi-node-2:2182,nifi-node-3:2183



#Enabling Clustering

nifi.cluster.is.node=true

nifi.cluster.node.address=nifi-node-1

nifi.cluster.node.protocol.port=8180



#Setting the NiFi Node Name

nifi.web.http.host=nifi-node-1

nifi.web.http.port=8080



#Site-to-Site protocol is used to distribute date between nodes in the cluster.

#Enabling Site-to-Site Protocol

nifi.remote.input.host=nifi-node-1

nifi.remote.input.socket.port=8280



#Property Used for Cluster Load Balancing (Only Available from NiFi 1.8.0+)

#Cluster Load Balancer will Redistribute Data from Failed NiFi Nodes

nifi.cluster.load.balance.host=nifi-node-1

nifi.cluster.load.balance.port=6342



#Property Used to Control the Starting of Cluster Election

nifi.cluster.flow.election.max.candidates=2



#NiFi Node 2 Properties



#Enabling Embedded Zookeeper

nifi.state.management.embedded.zookeeper.start=true



#Connection String of Embedded Zookeepers

nifi.zookeeper.connect.string=nifi-node-1:2181,nifi-node-2:2182,nifi-node-3:2183



#Enabling Clustering

nifi.cluster.is.node=true

nifi.cluster.node.address=nifi-node-2

nifi.cluster.node.protocol.port=8181



#Setting the NiFi Node Name

nifi.web.http.host=nifi-node-2

nifi.web.http.port=8081



#Site-to-Site protocol is used to distribute date between nodes in the cluster.

#Enabling Site-to-Site Protocol

nifi.remote.input.host=nifi-node-2

nifi.remote.input.socket.port=8281



#Property Used for Cluster Load Balancing (Only Available from NiFi 1.8.0+)

#Cluster Load Balancer will Redistribute Data from Failed NiFi Nodes

nifi.cluster.load.balance.host=nifi-node-2

nifi.cluster.load.balance.port=6343



#Property Used to Control the Starting of Cluster Election

nifi.cluster.flow.election.max.candidates=2



#NiFi Node 3 Properties



#Enabling Embedded Zookeeper

nifi.state.management.embedded.zookeeper.start=true



#Connection String of Embedded Zookeepers

nifi.zookeeper.connect.string=nifi-node-1:2181,nifi-node-2:2182,nifi-node-3:2183



#Enabling Clustering

nifi.cluster.is.node=true

nifi.cluster.node.address=nifi-node-3

nifi.cluster.node.protocol.port=8182



#Setting the NiFi Node Name

nifi.web.http.host=nifi-node-3

nifi.web.http.port=8082



#Site-to-Site protocol is used to distribute date between nodes in the cluster.

#Enabling Site-to-Site Protocol

nifi.remote.input.host=nifi-node-3

nifi.remote.input.socket.port=8282



#Property Used for Cluster Load Balancing (Only Available from NiFi 1.8.0+)

#Cluster Load Balancer will Redistribute Data from Failed NiFi Nodes

nifi.cluster.load.balance.host=nifi-node-3

nifi.cluster.load.balance.port=6344



#Property Used to Control the Starting of Cluster Election

nifi.cluster.flow.election.max.candidates=2



Step 5: Restart All NiFi Nodes



## Create a custom processor

See  nifi-custom-processors folder

mvn install on nifi-custom-processor

copy .nar file to \nifi-root-folder\lib (where nifi is installed)

Choose the custom processor from canvas (similar to other in-built processor)