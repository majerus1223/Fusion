# Fusion

Refrences to create, link and deploy various monitoring components.

### Prereqs
* Kubernetes deployment of some kind
    * Rancher Desktop, k3s, docker desktop, etc..

* In each values file update the "domain" to whatever you plan to use
    * Be sure to save the files 😉
* Setup DNS to point to your kubernetes enviroment
    * A records for loki, grafana, prometheus, pyroscope, tempo to the respective kubernetes host or cluster.

        * example: A record 192.168.1.180 -> loki.yourcustomdomain.com




### Configuration

* #### Step 1 - Add repos and update charts

      helm repo add grafana https://grafana.github.io/helm-charts
      helm repo add prometheus-community https://prometheus-community.github.io/helm-charts


      helm repo update

<br>

___
* #### Step 2 - Create your namespace/namespaces (Single or individual..)

      #Single Namespace 
      kubectl create namespace monitoring-fusion
      kubectl create namespace tempo-fusion   <- Required for the moment..

* ##### ☝️ or 👇

        # Individual Namespaces
        kubectl create namespace grafana-fusion
        kubectl create namespace loki-fusion
        kubectl create namespace tempo-fusion
        kubectl create namespace pyroscope-fusion
        kubectl create namespace prometheus-fusion
        kubectl create namespace alloy-fusion
<br>

___


* #### Step 3 - Deploy the stack (Single or individual..)


        # Single Namespace Deployment 
        helm -n monitoring-fusion upgrade --install loki grafana/loki -f values/loki-values.yaml
        helm -n monitoring-fusion upgrade --install grafana grafana/grafana -f values/grafana-values.yaml
        helm -n tempo-fusion upgrade --install tempo grafana/tempo-distributed -f values/tempo-values.yaml
        helm -n monitoring-fusion upgrade --install pyroscope grafana/pyroscope -f values/pyroscope-values.yaml
        helm -n monitoring-fusion upgrade --install prometheus prometheus-community/prometheus -f values/prometheus-values.yaml
        helm -n monitoring-fusion upgrade --install alloy  grafana/alloy -f values/alloy-values.yaml

* ##### ☝️ or 👇

        # Individual Namespace Deployment
        helm -n loki-fusion upgrade --install loki grafana/loki -f values/loki-values.yaml
        helm -n grafana-fusion upgrade --install grafana grafana/grafana -f values/grafana-values.yaml
        helm -n tempo-fusion upgrade --install tempo grafana/tempo-distributed -f values/tempo-values.yaml
        helm -n pyroscope-fusion upgrade --install pyroscope grafana/pyroscope -f values/pyroscope-values.yaml
        helm -n prometheus-fusion upgrade --install prometheus prometheus-community/prometheus -f values/prometheus-values.yaml
        helm -n alloy-fusion upgrade --install alloy  grafana/alloy -f values/alloy-values.yaml


<br>

___

### Helpful tips when things fail or ⛓️‍💥

 - Make sure you are in this repo's directory
 
        cd C:\Users\you\downloads\Path_to_fusion

- Verify nodes are up and running

        PS C:\Users\you> kubectl get nodes
        NAME    STATUS   ROLES                  AGE    VERSION
        9000x   Ready    control-plane,master   21d   v1.29.3+k3s1kubectl get nodes






