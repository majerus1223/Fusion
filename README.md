# Fusion

Refrences to create, link and deploy various monitoring components.

### Prereqs
* Kubernetes deployment of some kind
    * Rancher Desktop, k3s, docker desktop



### Configuration

* Add repos and update
    * `helm repo add grafana https://grafana.github.io/helm-charts`

    * `helm repo update`

    * `kubectl create namespace tempo-test`

* Create Namespaces (Single namespace, or individual..)
    * `kubectl create namespace monitoring-fusion` 

    * `kubectl create namespace grafana-fusion`
    * `kubectl create namespace loki-fusion`
    * `kubectl create namespace pyroscope-fusion`
    * `kubectl create namespace tempo-fusion`

* Install charts
    * Make sure you are in this directory
        * cd Path_to_fusion 
    * `helm -n loki-fusion install tempo grafana/loki -f values/loki-values.yaml`

    * `helm -n pyroscope-fusion install tempo grafana/pyroscope -f values/pyroscope-values.yaml`
    
    * `helm -n tempo-fusion install tempo grafana/tempo-distributed -f values/tempo-values.yaml`




