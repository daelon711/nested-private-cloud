# puppy vm creation

1. download TrixiePup64-Retro-2509.iso from [https://forum.puppylinux.com/puppy-linux-collection](https://forum.puppylinux.com/puppy-linux-collection)
    
    [https://sourceforge.net/projects/pb-gh-releases/files/TrixiePup64Retro_release/](https://sourceforge.net/projects/pb-gh-releases/files/TrixiePup64Retro_release/)
    
    [https://sourceforge.net/projects/pb-gh-releases/files/TrixiePup64Retro_release/TrixiePup64-Retro-2509-260901.iso](https://sourceforge.net/projects/pb-gh-releases/files/TrixiePup64Retro_release/TrixiePup64-Retro-2509-260901.iso)
    
2. pve-elene → local-btrfs → ISO Images → Download from URL
    
    write TrixiePup64-Retro-2509.iso in the name
    
3. from datacenter, tap create vm
    - **VMID**: 100
    - **Name**: `puppy-debian`
    - **OS**: select the ISO that was just downloaded
    - **System tab**: Machine type = **q35**
    - Disk size: 4 GiB - we have 19.5 GiB in total and 32 would eat 20 gib up
    - **CPU**: 2 sockets 1 core
    - CPU tyoe: qemu64
    - **Memory** : 512 MB
    - **Network**: default vmbr0
    
    ![image.png](puppy%20vm%20creation/image.png)
    
4. start vm
    
    ![image.png](puppy%20vm%20creation/image%201.png)
    
5. on host/ vm
    1. `ps aux | grep kvm`
    2. `qm list`- confirming vm running
    3. `qm showcmd 100`- launching command that proxmox used to start this vm, for detecting errors
    4. `ip a` - tap100i0 got added for puppy_debian
    
    ![image.png](puppy%20vm%20creation/image%202.png)
    
    ![image.png](puppy%20vm%20creation/image%203.png)
    
    ![image.png](puppy%20vm%20creation/image%204.png)
    

! if proxmox node 1 crashes puppy vm won’t be able to restart, to make it restart on the node 2 later **high availability** configuration is needed