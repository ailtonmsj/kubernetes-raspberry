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

## IMPORTANT!
### For test purpose use arg "kubelet-insecure-tls" in the metric-server deployment, the CA for node will be ignored

```yaml
...
template:
    metadata:
      labels:
        k8s-app: metrics-server
    spec:
      containers:
      - args:
        - --cert-dir=/tmp
        - --secure-port=4443
        - --kubelet-preferred-address-types=InternalIP,ExternalIP,Hostname
        - --kubelet-use-node-status-port
        - --metric-resolution=15s
        - --kubelet-insecure-tls
        image: k8s.gcr.io/metrics-server/metrics-server:v0.6.1
        imagePullPolicy: IfNotPresent
...
```

