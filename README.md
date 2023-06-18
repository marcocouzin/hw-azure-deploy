# Azure Deploy

### Azure initial set up

- CREATE A CLUSTER
```
az group create --name gpaksfiaptravel --location eastus && az aks create --name aksfiaptravel --resource-group gpaksfiaptravel --node-count 2 --generate-ssh-keys
```

- CONNECT TO CLUSTER THROUGH THE AZURE CLOUD SHELL
```
az aks get-credentials --resource-group gpaksfiaptravel --name aksfiaptravel
```

##### HELPFUL COMMANDS:

###### LIST THE CLUSTER'S NODE
```
kubectl get nodes 
```
```
kubectl get namespaces
```
```
kubectl get pod -A
```

### INSTALL THE WEAVE WORKS GRAPHIC ADMINISTRATIVE TOOL
```
kubectl apply -f https://github.com/weaveworks/scope/releases/download/v1.13.2/k8s-scope.yaml && kubectl patch svc weave-scope-app -n weave -p '{"spec": {"type": "LoadBalancer"}}'`
```
```
kubectl get svc -n weave
```