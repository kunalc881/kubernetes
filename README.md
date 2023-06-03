# kubernetes
# TO install Controlplane (Master) on your ubuntu machine from scratch follow the steps 
Run first script iptables-docker.sh
edit vi /etc/containerd/config.toml and change disabled_plugins ["ctr"]  to enable_plugins ["containerd"]
then run second script called master_kubeadm_init.sh

to create token to attach node just run the command

sudo kubeadm token create --print-join-command


# To install node on your ubuntu machine use the following steps

Run scrpit called iptables-docker.sh
edit vi /etc/containerd/config.toml and change disabled_plugins ["ctr"]  to enable_plugins ["containerd"]
Run a script called worker-node.sh 
then 
create token on your master machine by using command

sudo kubeadm token create --print-join-command
and run that token to node to connect to master
