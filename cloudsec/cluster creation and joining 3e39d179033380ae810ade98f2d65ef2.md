# cluster creation and joining

node 1 and node 2 become a part of the same datacenter

### node1

create cluster from: Datacenter → Cluster → Create Cluster

![image.png](cluster%20creation%20and%20joining/image.png)

take join information to later join the node2 in - tale base64

![image.png](cluster%20creation%20and%20joining/image%201.png)

go to node 2 and join cluster from datacenter, paste base64

![image.png](cluster%20creation%20and%20joining/image%202.png)

log in to node 2 as a user1 account, confirm what's visible

user1 can also now see the pve-elene of node 1 - user1's role assignment was likely granted at the datacenter level (path /)

puppy vm hasn’t migrated - sitting on pve-elene

![image.png](cluster%20creation%20and%20joining/image%203.png)

check on both nodes: pvecm status

![image.png](cluster%20creation%20and%20joining/image%204.png)

now that two nodes exist in the cluster - corosync is activated = quorum can be made

**quorate** = enough nodes are currently online and voting to safely make cluster-wide changes 

managed by quorosync

quorum calculation is counted by **corosync** and quorate happens