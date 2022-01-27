# FastAPI 




<br>

<p style="text-align:center">
<img src="https://d1.awsstatic.com/PAC/kuberneteslogo.eabc6359f48c8e30b7a138c18177f3fd39338e05.png" width="200" >
<img src="https://fastapi.tiangolo.com/img/logo-margin/logo-teal.png" width="200" > 
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/3/38/Prometheus_software_logo.svg/1200px-Prometheus_software_logo.svg.png" width="100">
<img src="https://upload.wikimedia.org/wikipedia/en/thumb/a/a1/Grafana_logo.svg/1200px-Grafana_logo.svg.png" width="100" >

</p>
<br>
<br> 

<p>
<p style="text-align:center">
<img src="assets/k8s.jpg" > 
</p>


This is a Kubernetes version of [reco-model-monitoring](https://github.com/silverstone1903/reco-model-monitoring) project. FastAPI, Grafana & Prometheus run on Kubernetes.


<br> <br>

## Installation

There is only one prerequisites:

* [Kubernetes](https://kubernetes.io/docs/tasks/tools/)

<br>

``` bash
git clone https://github.com/silverstone1903/reco-app-k8s
```

## Usage

### Start 

First create a namespace called `monitoring`.
```bash
kubectl create namespace monitoring
```

``` bash
kubectl apply -f manifests/.
```

Check pods, services and deployments

```bash
kubectl get pods -n monitoring --show-labels
kubectl get svc -n monitoring -o wide
kubectl get deployment -n monitoring -o wide
```


Scale a replicaset 
```bash
kubectl scale --replicas 3 deployment reco-app -n monitoring
```

### Logs
If you want to check pod logs with `kubectl` you can use `logs`.

``` bash
kubectl logs --selector app=reco-app -n monitoring
kubectl logs --selector app=grafana -n monitoring
kubectl logs --selector app=prometheus-server -n monitoring
```

### Stop & delete all resources

``` bash
kubectl delete -f manifests/.
kubectl delete ns monitoring
```

## URLs

* FastAPI: http://localhost:8000
* Prometheus: http://localhost:9090
* Grafana: http://localhost:3000



<!-- 
<br>

Blog post (in Turkish): [Reco Model Monitoring - FastAPI + Prometheus + Grafana](https://silverstone1903.github.io/posts/2021/12/reco-model-monitoring)

<br> -->

# Screenshots
## API
<p align="center">
  <img src="assets/api-response-item.png"  width="800">
  <img src="assets/api-response-user.png" width="800">
  <img src="assets/fastapidocs.png" width="800">
</p>

## Grafana
<p align="center">
  <img src="assets/grafana-1.png"  width="800">
  <img src="assets/grafana-2.png"  width="800">

</p>

