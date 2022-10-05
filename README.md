# PoC NX On-Prem

## Step 1 - Start the Minikube

```sh
minikube start
```

## Step 2 - Deploy MongoDB Kubernetes Operator

```sh
helm repo add mongodb https://mongodb.github.io/helm-charts
helm install community-operator mongodb/community-operator --namespace mongodb --create-namespace

kubectl apply -f mongodb.yml
kubectl get -n mongodb secret cloud-mongodb-nrwl-api-admin-user -o go-template='{{range $k,$v := .data}}{{"### "}}{{$k}}{{"n"}}{{$v|base64decode}}{{"nn"}}{{end}}'
```

## Step 3 - Enable Ingress for Minikube

```sh
minikube addons enable ingress
```


## Step 4 - Create a persistent volume


```sh
kubectl apply -f pv.yml
kubectl apply -f pvc.yml
```

## Step 5 - Create the NX Cloud

```sh
kubectl apply -f cloud.yml
```
