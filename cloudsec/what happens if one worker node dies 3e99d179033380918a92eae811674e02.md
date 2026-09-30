# what happens if one worker node dies?

1. check what is there now: kubectl get pods -o wide
    1. there’s 4 replicas 2 on worker 1 - 2 on worker 2 
        
        ![image.png](what%20happens%20if%20one%20worker%20node%20dies/image.png)
        
2. from proxmox, stop worker1 and then → kubectl get pods -o wide
3. after simulating crash, all of them will start running on worker 2, terminating on worker 1 
    
    ![image.png](what%20happens%20if%20one%20worker%20node%20dies/image%201.png)
    
4. starting worker 1 again, it will redistribute the replicas: kubectl get pods -o wide