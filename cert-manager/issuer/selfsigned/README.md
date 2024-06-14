
## The SelfSigned issuer doesn’t represent a certificate authority as such, but instead denotes that certificates will “sign themselves” using a given private key. In other words, the private key of the certificate will be used to sign the certificate itself.

##  This Issuer type is useful for bootstrapping a root certificate for a custom PKI (Public Key Infrastructure), or for otherwise creating simple ad-hoc certificates.

## There are important caveats - including security issues - to consider with SelfSigned issuers; in general you’d likely want to use a CA issuer rather than a SelfSigned issuer. That said, SelfSigned issuers are really useful for initially bootstrapping a CA issuer.


### To install
```bash
kubectl apply -f .
```

### To check the issuer:
```bash
kubectl get Clusterissuer
```
### Result:
| NAME               | READY |  AGE |
| cluster-issuer     | True  |  19s |
| selfsigned-issuer  | True  |  19s |

### To check the Certificates:
```bash
kubectl -n cert-managerget Certificate
```
### Result:
| NAME             | READY  | SECRET                  | AGE  |
| selfsigned-ca    | True   | selfsigned-root-secret  | 5m2s |

### To check the Secrets:
```bash
kubectl -n cert-manager get secret
```
### Result:
| NAME                   |  TYPE                  |  DATA  | AGE |
| selfsigned-root-secret |  kubernetes.io/tls     |  3     | 30s |
