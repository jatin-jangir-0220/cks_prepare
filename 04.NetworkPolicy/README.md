# Network Policy

![4](../images/4.png)

Official documentation：https://kubernetes.io/docs/concepts/services-networking/network-policies/

## Create a network policy to restrict mutual access between pods. The default policy is that pods can access each other in different namespaces.

### Create a default deny all ingress

### Create a default deny all egress

### Create a default deny all ingress, egress

```yaml
---
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: denypolicy
  namespace: testing
spec:
  podSelector: {}
  policyTypes:
  - Egress
  - Ingress
```

![4-1](../images/4-1.png)
```yaml
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: pod-access
  namespace: development
spec:
  podSelector:
    matchLabels:
      role: pod-xxx # pod的label
  policyTypes:
    - Ingress
  ingress:
    - from:
      - namespaceSelector:
          matchLabels:
            role: test # testing namespace 的label
    - from:
      - namespaceSelector: {} # 所有namespace
        podSelector:
          matchLabels:
            enviroment: staging
```

