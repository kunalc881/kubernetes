# Kubernetes
# TO install 1+1 cluster (One Master One Node) on your ubuntu machine using script follow the steps 
Prerequisites - your machine have minimum 2core CPU and 4GB RAM
and swap shouuld be off

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

Copy and Run this command on Master to create CNI (Container Network Interface) plugins (between master and node)
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

In this docs i have created 1+1 cluster (1 master and 1 cluster)
if you want to join multiple Nodes to your master you need to run that sh ubuntu_worker-node.sh script on those instances (machine)
and run that created token to Nodes which we created on master

# To install k8s cluster on your centos machine follow same process 
only replace the script 

To install Master Node run script
```
sh centos_master-node.sh
```

To install Worker Node run script
```
sh centos_worker-node.sh
```
after running both script 
run following command on master to create token 
```
 sudo kubeadm token create --print-join-command
```
Copy and Run this command on Master to create CNI (Container Network Interface) plugins (between master and node)
```
 kubectl apply -f https://github.com/weaveworks/weave/releases/download/v2.8.1/weave-daemonset-k8s.yaml
```

and check on master that your node is connected to master or not
In my case it is successfully connected to nodes and status is Ready 
```
[root@system1 ~]# kubectl get nodes -o wide
NAME      STATUS   ROLES           AGE   VERSION   INTERNAL-IP      EXTERNAL-IP   OS-IMAGE                KERNEL-VERSION                CONTAINER-RUNTIME
Master   Ready    control-plane   43m   v1.27.2   172.31.84.171   <none>        Centos Stream 8         4.18.0-408.el8.x86_64         containerd://1.6.21
Node1    Ready    <none>          32m   v1.27.2   172.31.92.10    <none>        Centos Stream 8         4.18.0-408.el8.x86_64         containerd://1.6.20
```
