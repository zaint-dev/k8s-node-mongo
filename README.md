vim ~/.aws/credentials

# Crear el namespace
```
kubectl apply -f namespace.yaml
```

# Ver la configuracion
```
kubectl config view
``` 

# Configurar el contexto
```
kubectl config set-context node-app-context --namespace=node-app-namespace --cluster=arn:aws:eks:us-east-1:492732896417:cluster/sharky-cluster --user=arn:aws:eks:us-east-1:492732896417:cluster/sharky-cluster

kubectl config use-context node-app-context
```

# Crear pods y servicios de mongo
```
kubectl apply -f mongo-node.yaml
kubectl get pods
kubectl get svc
```

# Crear replicaset, loadbalancer y servicio de la aplicación
```
kubectl apply -f node-app.yaml
kubectl get pods
kubectl get svc
kubectl get svc node-app
```

# Crear los volúmenes persistentes
```
kubectl apply -f persistent-volume.yaml
```

# Eliminar el servicio de mongo para realizar los cambios
```
kubectl delete -f mongo-node.yaml
```

# Crear el nuevo deployment de mongo
```
kubectl apply -f mongo-pv.yml
kubectl get pods
```