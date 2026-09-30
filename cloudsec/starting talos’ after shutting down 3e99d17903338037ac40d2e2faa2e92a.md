# starting talos’ after shutting down

Problem: kubectl get nodes failing with TLS certificate error

**reason:** x509: certificate signed by unknown authority even though the cluster itself (etcd, kubelet, port 6443) tested okay via talosctl. The kubeconfig file kubectl was reading (C:\Users\ekapa\.kube\config) had the correct server address but **mismatched certificate.**

**fix:** talosctl kubeconfig --talosconfig talosconf/talosconfig . --force
copy C:\Users\ekapa\kubeconfig C:\Users\ekapa\.kube\config -Force

fetching a new kubeconfig when the cluster was actually stable resolved it.

‼️shutting down a cluster ungracefully (instead of a clean `talosctl shutdown` per node) can leave boot-order and credential state inconsistent on restart