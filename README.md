# PoC NX On-Prem

## Step 1 - Deploy MongoDB Kubernetes Operator

- Make sure you already install Minikube and set Docker to have sufficient CPUs
- Create a persistent volume

```sh
helm repo add mongodb https://mongodb.github.io/helm-charts
helm install community-operator mongodb/community-operator --namespace mongodb --create-namespace
kubectl apply -f mongodb.yml
```
