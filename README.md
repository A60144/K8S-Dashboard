# K8S Dashboard


## Quickly to start

```
# Create for RBAC
kubectl create -f admin-user.yaml
kubectl create -f admin-user-role-binding.yaml
kubectl create -f open-api.yaml

# Create dashboard
kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v1.10.1/src/deploy/recommended/kubernetes-dashboard.yaml

# Create monitoring
## kubectl create -f https://raw.githubusercontent.com/kubernetes/heapster/master/deploy/kube-config/influxdb/influxdb.yaml
## kubectl create -f https://raw.githubusercontent.com/kubernetes/heapster/master/deploy/kube-config/influxdb/grafana.yaml
## kubectl create -f https://raw.githubusercontent.com/kubernetes/heapster/master/deploy/kube-config/influxdb/heapster.yaml
kubectl create -f https://raw.githubusercontent.com/kubernetes-retired/heapster/master/deploy/kube-config/influxdb/influxdb.yaml
kubectl create -f https://raw.githubusercontent.com/kubernetes-retired/heapster/master/deploy/kube-config/influxdb/grafana.yaml
kubectl create -f https://raw.githubusercontent.com/kubernetes-retired/heapster/master/deploy/kube-config/influxdb/heapster.yaml

# show pod
kubectl get po -n kube-system

heapster-xxxxx                  1/1       Running 
monitoring-grafana-xxxx         1/1       Running
monitoring-influxdb-xxxx        1/1       Running
```
```
# Show Token
kubectl -n kube-system describe secret $(kubectl -n kube-system get secret | grep admin-user | awk '{print $1}')

# Copy token
Name:         admin-user-token-c8xvl
Namespace:    kube-system
Labels:       <none>
Annotations:  kubernetes.io/service-account.name=admin-user
              kubernetes.io/service-account.uid=f1b7d105-a5e8-11e8-965e-141877616412
Type:  kubernetes.io/service-account-token
Data
====
ca.crt:     1419 bytes
namespace:  11 bytes
token:      eyJhbGciOiJSUzI1NiIsImtpZCI6IiJ9.eyJpc3....
```

```
# Login with paste token
https://localhost:6443/api/v1/namespaces/kube-system/services/https:kubernetes-dashboard:/proxy/#!/overview?namespace=default
```
![](https://i.imgur.com/t0uiytF.png)


![](https://i.imgur.com/oj9g1uM.png)


ref:
* https://github.com/kubernetes/dashboard
* https://github.com/kubernetes/heapster/tree/master/deploy/kube-config/influxdb
* https://www.cnblogs.com/RainingNight/p/deploying-k8s-dashboard-ui.html
