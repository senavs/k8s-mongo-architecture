# Kubernetes mongo architeture

Kubernetes base configuration architeture with mongodb and mongo-express

## Subjects
To create this mongo project architeture, the following Kubernetes components are used.
  - Namespaces
  - Pods
  - Deployment
  - Services (Internal and External)
  - Secrets
  - ConfigMaps
  - Ingress
  - _minikube_


## Seting up
To start settingup this project architeture, it's necessary to create a new `namespace` with the following command.
```sh
kubectl create namespace prod-mongo
```

Then, before setup the pods and deployments, it's necessary to create all `secrets` and `config maps`.
```sh
kubectl apply -f namespace-secret.yaml
kubectl apply -f namespace-configmap.yaml
```

After set all base configs, now it's time to deploy `mongo` and `mongo-express` containers inside the cluster.
With that said, the `deployment` and `pod` can be applied.
```sh
kubectl apply -f mongo-database/mongo-database-deployment.yaml
kubectl apply -f mongo-express/mongo-express-deployment.yaml
```

Finally, the `services` and `ingress` can be setup.
```sh
kubectl apply -f mongo-database/mongo-database-service.yaml
kubectl apply -f mongo-express/mongo-express-service.yaml
```
```sh
kubectl apply -f namespace-ingress.yaml
```

## Testing
You can test the project by accessing ingress `IP address`.
```sh
kubectl get ingress -n prod-mongo
```
