# Two ways to install certmanager:

## "Kubectl Way"

### "apply" folder has a manisfests to install a cert-manager by kubectl apply

## "Helm Way"

### "helm" folder has the instructions to install cert-manager by helm 

# Configure
## "issuer" folder has the issuer manifests to configure the Issuer (selfSigned), execute afet configure certmanager


### To check the certmanager instalation:
```bash
kubectl get pods --namespace cert-manager
```

### Must have 3 containers in running state:

| NAME                                    |  READY |  STATUS  |  RESTARTS |  AGE |
| ---                                     |  ---   |  ---     |  ---      |  --- |
| cert-manager-848f547974-khz6p           |  1/1   |  Running |  0        |  76s |
| cert-manager-cainjector-54f4cc6b5-h9c49 |  1/1   |  Running |  0        |  76s |
| cert-manager-webhook-58fb868868-4xpxv   |  1/1   |  Running |  0        |  75s |