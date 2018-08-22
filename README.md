# K8S Dashboard


## Quickly to start

```
# For RBAC
kubectl create -f admin-user.yaml
kubectl create -f admin-user-role-binding.yaml
kubectl create -f open-api.yaml


# Creat dashboard
kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/master/src/deploy/recommended/kubernetes-dashboard.yaml
 
# Create monitoring
kubectl create -f https://raw.githubusercontent.com/kubernetes/heapster/master/deploy/kube-config/influxdb/influxdb.yaml
kubectl create -f https://raw.githubusercontent.com/kubernetes/heapster/master/deploy/kube-config/influxdb/grafana.yaml
kubectl create -f https://raw.githubusercontent.com/kubernetes/heapster/master/deploy/kube-config/influxdb/heapster.yaml

kubectl get po -n kube-system

# show
heapster-xxxxx                  1/1       Running 
monitoring-grafana-xxxx         1/1       Running
monitoring-influxdb-xxxx        1/1       Running

 
# Show Token & Copy token
kubectl -n kube-system describe secret $(kubectl -n kube-system get secret | grep admin-user | awk '{print $1}')

# Resault & Copy token
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
token:      eyJhbG....


# Login with paste token
https://localhost:6443/api/v1/namespaces/kube-system/services/https:kubernetes-dashboard:/proxy/#!/overview?namespace=default
```
