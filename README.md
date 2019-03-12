# kubernetes-orangesys-telegraf

## How to monitoring kubernetes use orangesys

### create monitoring namespace

```sh
kubectl create namespace monitoring
```

### create secret with telegraf configmap

```sh
kubectl create secret -n monitoring generic telegraf --from-literal=env=prod --from-literal=orangesys_url=https://demo.i.orangesys.io --from-literal=jwt_token=<your-orangesys-token>
```

### Create kubernetes daemonset

```sh
kubectl apply -f configmap.yaml
kubectl apply -f daemonset.yaml
```
