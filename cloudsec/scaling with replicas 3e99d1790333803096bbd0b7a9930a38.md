# scaling with replicas

Scaling proves the scheduler can spread one workload across multiple machines automatically, k8s decides which machine takes which replica/pod

1. create 4 replicas: kubectl scale deployment first-workload-nginx --replicas=4
2. check: kubectl get pods -o wide
    
    ![image.png](scaling%20with%20replicas/image.png)
    
3. it’s running on 4 IPs now, make it reachable only with 1 IP, “expose deployment”: kubectl expose deployment first-workload-nginx --port=80 --type=NodePort
    1. kubectl get services
        
        ![image.png](scaling%20with%20replicas/image%201.png)
        
    2. kubectl port-forward services/first-workload-nginx 9000:80
    3. nginx runs on 80 inside the pod → NodePort exposes it cluster-wide on 30677 → port-forward is a separate temporary tunnel made on 9000
    4. scroll to → localhost:9000
        
        ![image.png](scaling%20with%20replicas/image%202.png)
        

1. **Scale the deployment** - making Kubernetes create 4 copies instead of 1, with kubectl scale.
2. **Scheduler places the new pods** - decides which node each of the 3 new pods should land on, spreading them across workers.
3. **CNI assigns each new pod an IP** 
4. **Pods go Running** - now you have 4 separate running copies of nginx.
5. **kubectl get pods -o wide** - check the NODE column to confirm they actually spread across talos-worker1 and talos-worker2