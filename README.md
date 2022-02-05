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