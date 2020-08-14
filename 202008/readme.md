# Kubernetes Dashboard
```shell=
kubectl create -f dashboard-admin.yaml
kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.0.3/aio/deploy/recommended.yaml
```
https://github.com/kubernetes/dashboard
```shell=
kubectl create -f admin-user-svc.yaml
kubectl create -f admin-user-crb.yaml
kubectl -n kubernetes-dashboard describe secret $(kubectl -n kubernetes-dashboard get secret | grep admin-user | awk '{print $1}')

kubectl proxy
```
https://github.com/kubernetes/dashboard/blob/master/docs/user/access-control/creating-sample-user.md

```shell=
## use browser
http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/
```

