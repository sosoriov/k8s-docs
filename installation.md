Ubuntu 18.04

## Steps:

1. Upgrade packages:

```
sudo -i

apt-get update && apt-get upgrade -y
```

2. Install Docker

```
apt-get install docker.io -y
```

3. Add Kubernetes xenial repository

```
vim /etc/apt/sources.list.d/kubernetes.list
```

inside the file, add:

*deb http://apt.kubernetes.io/ kubernetes-xenial main*

4. Adding GPG

```
curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg \
| apt-key add -
```

5. Update the repo

```
apt-get update
```

6. Install Kubeadmin, Kubectl and Kubelet

```
apt-get install -y \
kubelet=1.14.1-00 kubectl=1.14.1-00 kubeadm=1.14.1-00
```

7. Decide the CNI (Container Network Interface)

In this case I used Calico

> download yaml files for configuration

TODO: check this

8. Start Docker service

```
systemctl enable docker.service 
```

9. Initialize master node

```
kubeadm init --kubernetes-version 1.14.1 \
--pod-network-cidr 192.168.0.0/16 \
| tee kubeadm-init.out
```

TODO: add Kubectl config file
