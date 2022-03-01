# To deploy the Nginx Ingress Gateway (version >= 1.22):

```bash
kubectl apply -f ./kube-metrics/
```

## Validate:

```bash
kubectl get po -n kube-system
```

### The result should be something like it ( Exposing using NodePort instead LoadBalancer ): 

| NAME                               | READY    | STATUS    | RESTARTS  | AGE  |
| ---                                | ---      | ---       | ---       | ---  |
| ...                                | ...      | ...       | ...       | ...  |
| metrics-server-85c456c8d8-2fc9l    | 1/1      | Running   | 0         | 4m9s |
| ...                                | ...      | ...       | ...       | ...  |

<br/>

