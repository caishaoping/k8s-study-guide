# CKA  Practice Tasks 

## Use Kubeadm to install a basic cluster

## Consider working through Kubernetes the hard way


## Perform a version upgrade on a Kubernetes cluster using Kubeadm

## Implement etcd backup and restore

## Learn to troubleshoot a worker node

sudo -i
  systemctl status kubelet
  root@worker-1:~# systemctl status kubelet
  kubelet.service - kubelet: The Kubernetes Node Agent
   Loaded: loaded (/lib/systemd/system/kubelet.service; enabled; vendor preset: enabled)
  Drop-In: /etc/systemd/system/kubelet.service.d
           └─10-kubeadm.conf
   Active: active (running) since Sat 2022-06-11 21:16:54 UTC; 4h 52min ago
     Docs: https://kubernetes.io/docs/home/
 Main PID: 743 (kubelet)
    Tasks: 13 (limit: 545)
   CGroup: /system.slice/kubelet.service
           ├─  743 /usr/bin/kubelet --bootstrap-kubeconfig=/etc/kubernetes/bootstrap-kubelet.conf --kubeconfig=/etc/kubernetes/kubelet.co
           └─12270 /usr/bin/kubelet --bootstrap-kubeconfig=/etc/kubernetes/bootstrap-kubelet.conf --kubeconfig=/etc/kubernetes/kubelet.co

Jun 12 02:07:25 worker-1 kubelet[743]: E0612 02:07:25.723908     743 summary_sys_containers.go:47] "Failed to get system container stats"
Jun 12 02:07:35 worker-1 kubelet[743]: E0612 02:07:35.740580     743 summary_sys_containers.go:47] "Failed to get system container stats"
Jun 12 02:07:45 worker-1 kubelet[743]: E0612 02:07:45.763603     743 summary_sys_containers.go:47] "Failed to get system container stats"
Jun 12 02:07:55 worker-1 kubelet[743]: E0612 02:07:55.773314     743 summary_sys_containers.go:47] "Failed to get system container stats"
Jun 12 02:08:05 worker-1 kubelet[743]: E0612 02:08:05.791175     743 summary_sys_containers.go:47] "Failed to get system container stats"
Jun 12 02:08:15 worker-1 kubelet[743]: E0612 02:08:15.803485     743 summary_sys_containers.go:47] "Failed to get system container stats"
Jun 12 02:08:25 worker-1 kubelet[743]: E0612 02:08:25.812326     743 summary_sys_containers.go:47] "Failed to get system container stats"
Jun 12 02:08:35 worker-1 kubelet[743]: E0612 02:08:35.864761     743 summary_sys_containers.go:47] "Failed to get system container stats"
Jun 12 02:08:45 worker-1 kubelet[743]: E0612 02:08:45.918095     743 summary_sys_containers.go:47] "Failed to get system container stats"
Jun 12 02:08:55 worker-1 kubelet[743]: E0612 02:08:55.969946     743 summary_sys_containers.go:47] "Failed to get system container stats"
lines 1-22/22 (END)

## Learn how to consult container logs directly with docker

## Learn how to consult resources in the kube-system namespace



  
