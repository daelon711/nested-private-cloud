# building Talos inside proxmox

https://github.com/siderolabs/talos/releases/latest/download/metal-amd64.iso

1. **create vm:**
    
    VMID: 200
    
    Name: talos-control (control runs API / front door for communication to receive cluster commands)
    
    Machine type: q35
    
    Disk:6 GB
    
    CPU:2 cores
    
    Memory: 3072 MB = 3GB (1.5GB for workers (1.5x1024MB))
    
    Network - default bridge to let vms sit on the same network as proxmox node: vmbr0
    
    ![image.png](building%20Talos%20inside%20proxmox/image.png)
    
2. start the console
    
    ![image.png](building%20Talos%20inside%20proxmox/image%201.png)
    
3. to create talos-workers, clone control by right click → clone
    
    ![image.png](building%20Talos%20inside%20proxmox/image%202.png)
    
4. start control first, then workers
5. configure network fn + f3 →

| Setting | talos-control |
| --- | --- |
| Hostname | `talos-control` |
| IP address | `192.168.169.200/24` |
| Gateway | `192.168.169.2` |
| DNS | `8.8.8.8` |

![image.png](building%20Talos%20inside%20proxmox/image%203.png)

| Setting | talos-worker-1 |
| --- | --- |
| Hostname | `talos-worker-1` |
| IP address | `192.168.169.201/24` |
| Gateway | `192.168.169.2` |
| DNS | `8.8.8.8` |

| Setting | talos-worker-2 |
| --- | --- |
| Hostname | `talos-worker-2` |
| IP address | `192.168.169.202/24` |
| Gateway | `192.168.169.2` |
| DNS | `8.8.8.8` |
1. ping from host to the talos’ ips 
    
    ![image.png](building%20Talos%20inside%20proxmox/image%204.png)
    

**so now we can work from our host and make changes to talos that lives on proxmox :)**