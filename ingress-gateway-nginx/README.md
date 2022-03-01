# To deploy the Nginx Ingress Gateway (version >= 1.22):

```bash
kubectl apply -f ./ingress-gateway-nginx
```

# To verify the Nginx Pod for Ingress:

```bash
kubectl get pod -n ingress-nginx
```
### The result should be something like it: 

| NAME                                      | READY | STATUS    | RESTARTS | AGE |
| ---                                       | ---   | ---       | ---      | --- |
| ingress-nginx-admission-create--1-ts7x9   | 0/1   | Completed | 0        | 90s |
| ingress-nginx-admission-patch--1-ksb4n    | 0/1   | Completed | 0        | 90s | 
| ingress-nginx-controller-54d8b558d4-qvf9s | 1/1   | Running   | 0        | 98s | 

<br/>

# To get the Ingress port for Nginx:

```bash
kubectl get svc -n ingress-nginx
```

### The result should be something like it ( Exposing using NodePort instead LoadBalancer ): 

| NAME                               | TYPE      | CLUSTER-IP    | EXTERNAL-IP | PORT(S)                    | AGE |
| ---                                | ---       | ---           | ---         | ---                        | --- |
| ingress-nginx-controller           | NodePort  | 10.111.205.37 | <none>      | 80:31402/TCP,443:31337/TCP | 76s |
| ingress-nginx-controller-admission | ClusterIP | 10.103.165.96 | <none>      | 443/TCP                    | 76s |

<br/>

### To access the cluster, use the kubernetes cluster ip in browswer using the NodePort, it will return 404 http status code becase doesn't exist Ingress configuration to any backend ( service ):

```bash
http://<KUBERNETES-NODE-IP>:<HTTP-NODE-PORT>
https://<KUBERNETES-NODE-IP>:<HTTPS-NODE-PORT>
```

### Example:
```bash
http://192.168.0.100:31402
https://192.168.0.100:31337
```

# To deploy a test for Ingress Controller:
```bash
kubectl apply -f ./ingress-gateway-nginx/example-to-test/
```

### To access:
```bash
http://<CLUSTER-NODE-IP>:<HTTP-INGRESS-PORT>/httpd
http://<CLUSTER-NODE-IP>:<HTTP-INGRESS-PORT>/nginx
```

### Example:
```bash
http://192.168.0.100:31402/httpd
http://192.168.0.100:31402/nginx
```
