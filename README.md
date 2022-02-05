# How to run
```
kubectl apply -f k8s
kubectl get pods
kubectl get deployments
```

* open browser at `http://localhost` or `https://localhost`

# How to stop
```
kubectl delete -f k8s
```

<br/><br/>

# k8s dashboard

## How to start
follow the steps here from [k8s docs](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/#deploying-the-dashboard-ui)

* start dashboard

```
kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.4.0/aio/deploy/recommended.yaml
kubectl apply -f k8s/dash-admin-user.yaml
kubectl apply -f k8s/dash-clusterrole.yaml
kubectl proxy
```

* open browser: http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/
  * if you see empty dashboard, log out then log in again with the token in the next step

* get token
```
kubectl -n kubernetes-dashboard get secret $(kubectl -n kubernetes-dashboard get sa/admin-user -o jsonpath="{.secrets[0].name}") -o go-template="{{.data.token | base64decode}}"
```

## How to stop

```
kubectl delete -f k8s/dash-admin-user.yaml
kubectl delete -f k8s/dash-clusterrole.yaml
kubectl proxy
```

<br/><br/>

# Useful commands
```bash
kubectl get services
kubectl delete service/client-node-port
kubectl apply -f k8s/

kubectl get pv  # persistent volume
kubectl get pvc

kubectl create secret generic pgpassword --from-literal PGPASSWORD=password123
kubectl get secrets
```

* before using `ingress-nginx`, need to execute this?
```
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.1.1/deploy/static/provider/cloud/deploy.yaml
```