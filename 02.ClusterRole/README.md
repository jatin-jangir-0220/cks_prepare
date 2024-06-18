# Clusterrole

Modify the permissions of the role under the namespace to only allow list operations on certain types of objects. Create a new serviceaccount (sa02). Create a role named role02, and bind role02 through rolebinding. Only update operations on persistent volume claims are allowed.

```shell
1. 修改对应的role使用list权限

2. kubectl create sa sa01

3. kubectl create role role02 --verb=update

4. kubectl create rolebinding xxx-rolebinding --role role02 --serviceaccount namespace:sa02
```
