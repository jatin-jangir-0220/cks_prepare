# AppArmor

![5](../images/5.png)

## Documentation：https://kubernetes.io/docs/tutorials/security/apparmor/


## Create the profile used by AppArmor on the node node and load the profile file

```shell
apparmor_parser -q /etc/apparmor.d/nginx_apparmor

apparmor_status | grep nginx
```

## Create pod

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: hello-apparmor
  annotations:
    container.apparmor.security.beta.kubernetes.io/hello: localhost/nginx_apparmor # The focus is on hello’s container and localhost/nginx_apparmor
spec:
  containers:
  - name: hello #和上面的hello对应
    image: busybox:1.28
    command: [ "sh", "-c", "echo 'Hello AppArmor!' && sleep 1h" ]
```
