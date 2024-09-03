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
