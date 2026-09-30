# live migration of puppy vm

moving a VM's actual running state

1. deatach iso from vm 100 puppy vm  on node 1 
    1. VM 100 → Hardware → CD/DVD Drive → Edit → Do not use any media

1. right click vm and migrate:
    1. target node - pve (node2)
    2. Allow local disk migration - storage isnt shared between nodes 

![image.png](live%20migration%20of%20puppy%20vm/image.png)

1. run `qm list` on both nodes

![image.png](live%20migration%20of%20puppy%20vm/image%201.png)

nothing on node 1 

![image.png](live%20migration%20of%20puppy%20vm/image%202.png)

puppy vm on node 2

1. on web ui

![image.png](live%20migration%20of%20puppy%20vm/image%203.png)