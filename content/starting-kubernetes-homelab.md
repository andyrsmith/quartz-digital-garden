---
title: Set up a Kubernetes Homelab
date: 04/08/2026
tags:
  - homelab
  - kubernetes
links:
id: "202604080759"
---
# Set up a Kubernetes Homelab

To get started with a Kubernetes homelab you will need at least 2 different machines.  These can be mini pcs, old laptops, or raspberry pis, so just see what you have around already before you decide to buy anything.  I am using an old laptop and a raspberry pi.  

Pick a Linux distro without a GUI.  We can just ssh into these machines once they are setup so no need to have a GUI.  For the laptop I am using Ubuntu server and the Raspberry PI I am using Raspberry PI OS lite.

After the OS is install I would make sure you can SSH into both.  That way we don't have to have a keyboard and monitor hooked up to each.

For the laptop it would be nice to be able to close the lid without it going to sleep.  In /etc/systemd/logind.conf either add or update the following values. (These instructions work on Ubuntu server.  Should work on other distros with systemd)

```
HandleLidSwitch=ignore
LidSwitchIgnoreInhibited=no
```

Then restart the systemd-logind service

```
sudo service systemd-logind restart
```

After that you should be able to close the lid and the laptop will not go to sleep.  

K3s is a lightweight version of Kubernetes that is great to get started with.  Since my laptop has the better specs then the raspberry pi, so I will use that as my control plane. 
SSH into machine and install k3s with the following command.

```
curl -sfL https://get.k3s.io | sh - 
# Check for Ready node, takes ~30 seconds 
sudo k3s kubectl get node 
```

When setting up the agent we will need a token from our control plane. Get token from k3s so that the agent can connect to it.

```bash
sudo cat /var/lib/rancher/k3s/server/node-token
```


SSH into your other machine to install the agent with the token you retrieved. 

```
curl -sfL https://get.k3s.io | \
  K3S_URL=https://<control-plane-ip>:6443 \
  K3S_TOKEN=<YOUR_TOKEN> \
  sh -
```

After the control plane and agent has been setup you might want to update your dev computer so that you can use the kubectl command from it to connect to the cluster.  

On control plane view the file /etc/rancher/k3s/k3s.yaml then you can copy that file to your .kube directory on your dev machine with filename config.  

If the control plane didn't have a file at that location then running the config view command should output the location of that file.

```
kubectl config view
```

Once config file is setup then test the cluster by running a kubectl commend

```
kubectl get nodes
```

This should output the control plane and agent.  Now you should be able to deploy application to your cluster.