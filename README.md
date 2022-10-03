# PoC NX On-Prem

## Step 1 - Deploy MongoDB Kubernetes Operator

- Make sure you already install Minikube and set Docker to have sufficient CPUs (`minikube config set cpus N`)
- Create a persistent volume

```sh
helm repo add mongodb https://mongodb.github.io/helm-charts
helm install community-operator mongodb/community-operator --namespace mongodb --create-namespace

kubectl apply -f mongodb.yml
kubectl get -n mongodb secret cloud-mongodb-nrwl-api-admin-user -o go-template='{{range $k,$v := .data}}{{"### "}}{{$k}}{{"n"}}{{$v|base64decode}}{{"nn"}}{{end}}'

minikube addons enable ingress

kubectl apply -f pv.yml
kubectl apply -f pvc.yml
kubectl apply -f cloud.yml
```
