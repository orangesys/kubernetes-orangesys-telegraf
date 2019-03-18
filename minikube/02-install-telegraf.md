# Install telegraf in minikube with GCP

## What is Telegraf?

[Introduction to Telegraf](https://docs.influxdata.com/telegraf/v1.3)

## Install Telegraf

Set the minikube cluster IP address:

```sh
minikube ip
```

Change telegraf configmaps with minikube ip address

```sh
cat configmap.yaml
...
    [[inputs.kubernetes]]
      url = "http://<MINIKUBE-IP>:10255"
      bearer_token = "/var/run/secrets/kubernetes.io/serviceaccount/token"
      insecure_skip_verify = true 
...
```

create secret with telegraf configmap

```sh
kubectl create secret -n monitoring generic telegraf --from-literal=env=prod --from-literal=orangesys_url=https://demo.i.orangesys.io --from-literal=jwt_token=<your-orangesys-token>
```

Install telegraf using helm:

```sh
kubeclt apply -f configmap.yaml
kubectl apply -f daemonset.yaml
```

Verify telegraf is running:

```sh
kubectl get pods -n monitoring
```

## Import dashboard to Orangesys dashboard

https://grafana.com/dashboards/9111
https://grafana.com/dashboards/2577
