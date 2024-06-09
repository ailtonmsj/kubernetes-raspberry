# Install Calico CNI plugin

## Use kubectl create/replace instead apply on the 00-install-operator
#### Before apply make sure the cidr block on file "00-install-operator.yaml" is equal your cluster configuration "--pod-network-cird" on kubelet or "--cluster-cidr" in kube-controller 

```bash
kubectl replace -f .
```

### important that calico does not work with others CNI plugins (except flannel) installed on /opt/cni/bin and /etc/cni/net.d.

#### I had the follow issue on coredns:
```bash
... plugin type="calico" failed (add): failed to create host netlink handle: protocol not supported 
```
#### solved install the some extra modules:
```bash
apt install linux-modules-extra-raspi
```