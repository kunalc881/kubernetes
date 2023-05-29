# kubernetes
# TO install Controlplane (Master) on your ubuntu machine from scratch follow the steps 
Run first script iptables-docker.sh
edit vi /etc/containerd/config.toml and change disabled_plugins ["ctr"]  to enable_plugins ["containerd"]
then run second script called master-kubeadm-init.sh

# To install node on your ubuntu machine use the following steps

Run scrpit called iptables-docker.sh
edit vi /etc/containerd/config.toml and change disabled_plugins ["ctr"]  to enable_plugins ["containerd"]
