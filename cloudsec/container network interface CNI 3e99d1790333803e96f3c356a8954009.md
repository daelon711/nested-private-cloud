# container network interface CNI

installs Flannel interface, giving Kubernetes pods its own IP address and builds the routing so pods on *different* nodes can reach each other

Kubernetes control node tells nodes which pods to run. pod is a thingy that’s being run = tasks

at this point, if there were two pods installed, there would be no way of them to communicate

that’s what CNI is for

Flannel auto detects the pod ip ranges that k8s already assigned per node

1. install flannel: kubectl apply -f [https://github.com/flannel-io/flannel/releases/latest/download/kube-flannel.yml](https://github.com/flannel-io/flannel/releases/latest/download/kube-flannel.yml) - getting back the warning: Pod Security admission controller commenting that Flannel's pods need elevated privileges
2. check node and pod status: kubectl get pods -n kube-flannel
    1. it’s going to be pending or container creating for a while and then after reaching running state→
    2. kubectl get nodes
    
    ![image.png](container%20network%20interface%20CNI/image.png)
    
3. deploy nginx to check that first actual nginx application workload will run: kubectl create deployment first-workload-nginx --image=nginxdemos/hello - deploys one single pod
    1. kubectl get nodes -o wide - to check which node nginx is running on, with its own internal IP
        
        ![image.png](container%20network%20interface%20CNI/image%201.png)
        

what has been done by now:

1. **Cluster created** - Kubernetes takes a big pod IP range and gives range per node.
2. **Pod requested** is requested to be run by user or kubernetes
3. **Scheduler picks a node** - decides which node that pod should live on.
4. **CNI (Flannel) assigns the pod an IP** - from that node's range, and builds routing so it can reach other pods.
5. **Pod goes Running** - now reachable by its pod IP, from any node in the cluster.