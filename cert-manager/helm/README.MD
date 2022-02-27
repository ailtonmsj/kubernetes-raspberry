# Install cert-manager with helm
  
## Create a namespace
```bash
kubectl create namespace cert-manager
```
  
## Add the Jeststack repo
```bash
helm repo add jetstack https://charts.jetstack.io
```
  
## Update helm repos
```bash
helm repo update
```
  
## Install cert-manager and CRDs from jetstack repo
```bash
helm install cert-manager jetstack/cert-manager --namespace cert-manager --create-namespace --version v1.4.0 --set installCRDs=true
```
  
## Verify the installation

```bash
kubectl get pods --namespace cert-manager
```

### Must have 3 containers in running state:

| NAME                                    |  READY |  STATUS  |  RESTARTS |  AGE |
| ---                                     |  ---   |  ---     |  ---      |  --- |
| cert-manager-848f547974-khz6p           |  1/1   |  Running |  0        |  76s |
| cert-manager-cainjector-54f4cc6b5-h9c49 |  1/1   |  Running |  0        |  76s |
| cert-manager-webhook-58fb868868-4xpxv   |  1/1   |  Running |  0        |  75s |
  
## Create a CA Issuer (Selfsigned)
```bash
kubectl apply -f ./issuer/selfsigned/
```

## Verify the certificate
```bash
kubectl -n cert-manager-selfsigned get issuer
```

```bash
kubectl -n cert-manager-selfsigned get certificate
```

```bash
kubectl -n cert-manager-selfsigned get certificaterequest
```

```bash
kubectl -n cert-manager-selfsigned get secret
```

### source: https://cert-manager.io/docs/installation/kubernetes/