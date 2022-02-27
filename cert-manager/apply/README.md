## To install:
```bash
kubectl apply -f .
```

## To check the certmanager instalation:
```bash
kubectl get pods --namespace cert-manager
```

### Must have 3 containers in running state:

| NAME                                    |  READY |  STATUS  |  RESTARTS |  AGE |
| ---                                     |  ---   |  ---     |  ---      |  --- |
| cert-manager-848f547974-khz6p           |  1/1   |  Running |  0        |  76s |
| cert-manager-cainjector-54f4cc6b5-h9c49 |  1/1   |  Running |  0        |  76s |
| cert-manager-webhook-58fb868868-4xpxv   |  1/1   |  Running |  0        |  75s |