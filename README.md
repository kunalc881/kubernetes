# kubernetes
# TO install Controlplane (Master) on your ubuntu machine from scratch follow the steps 
Run a following script called ubuntu_master-node.sh to install master on your instance
then create token to join the worker node to master using command

to create token to attach node just run the command
```
 sudo kubeadm token create --print-join-command
```
copy the token and paste it to your node you want to connect to your master
after that run the following command to create CNI plugins between cluster (master and node)

```
 kubectl apply -f https://github.com/weaveworks/weave/releases/download/v2.8.1/weave-daemonset-k8s.yaml
```

# To install node on your ubuntu machine use the following steps

Run following script called ubuntu_worker-node.sh to install Worker Node 
```
sh ubuntu_worker-node.sh
```
