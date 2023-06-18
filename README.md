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

#
### INSTALL THE WEAVE WORKS GRAPHIC ADMINISTRATIVE TOOL
```
kubectl apply -f https://github.com/weaveworks/scope/releases/download/v1.13.2/k8s-scope.yaml && kubectl patch svc weave-scope-app -n weave -p '{"spec": {"type": "LoadBalancer"}}'`
```
```
kubectl get svc -n weave
```

#

### SET UP THE PROJECT DEPLOY STRUCTURE
- DOWNLOAD THE DEPLOYMENT PROJECT
```
git clone https://github.com/marcocouzin/hw-azure-deploy.git
```
- CHECK THE DEPLOY FILE
```
cd hw-azure-deploy/fed_deploy
```
```
cat fed_deploy.yml
```
- CREATE THE DEPLOYMENT
```
kubectl create -f fed_deploy.yml 
```
### EXPOSE THE SERVICE THROUGH A LOAD BALANCER


cat svc_page_loadbalancer.yml


az aks delete --yes --name aksfiaptravel --resource-group gpaksfiaptravel && az group delete --yes --resource-group gpaksfiaptravel