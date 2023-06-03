# Kubernetes
# TO install Controlplane (Master) on your ubuntu machine from scratch follow the steps 
Download the scripts using command
```
git clone https://github.com/kunalc881/kubernetes
cd kubernetes
```

Run a following script called ubuntu_master-node.sh to install master on your instance
```
sh ubuntu_master-node.sh
```
Run script ubuntu_worker-node.sh to install worker node on your instance
```
sh ubuntu_worker-node.sh
```
To create token on master to  join the worker node to master use command
```
 sudo kubeadm token create --print-join-command
```
copy the created token and paste it to your node you want to connect to your master 

Create CNI (Container Network Interface) plugins between (master and node) using command
```
 kubectl apply -f https://github.com/weaveworks/weave/releases/download/v2.8.1/weave-daemonset-k8s.yaml
```

and check on master that your node is connected to master or not
In my case it is successfully connected to nodes and status is Ready 
```
[root@system1 ~]# kubectl get nodes -o wide
NAME      STATUS   ROLES           AGE   VERSION   INTERNAL-IP      EXTERNAL-IP   OS-IMAGE                KERNEL-VERSION                CONTAINER-RUNTIME
system1   Ready    control-plane   43m   v1.27.2   192.168.10.130   <none>        ubuntu 20.04.6 LTS         4.18.0-486.el8.x86_64         containerd://1.6.21
system2   Ready    <none>          32m   v1.27.2   192.168.10.128   <none>        ubuntu 20.04.6 LTS   3.10.0-1160.88.1.el7.x86_64   containerd://1.6.20
```

# To install node on your ubuntu machine use the following steps

Run following script called ubuntu_worker-node.sh to install Worker Node 
```
sh ubuntu_worker-node.sh
```
