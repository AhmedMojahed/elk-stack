# elk-stack

This repo is a test for deploying elk stack w/ kafka

## Note:

This deployment is using helm charts on top of kubernetes minikube for testing only you can tweak the values and deploy it on your own cluster

## Prerequisits

- helm
- kubectl
- minikube (or configure your kubectl on you testing environment)

## first without kafka

Deployment is in the order mentioned in elasitc.co['https://www.elastic.co/guide/en/elastic-stack/current/installing-elastic-stack.html#install-order-elastic-stack'] docs

1. add the elastic repo in helm

```
helmhelm repo add elastic https://helm.elastic.co
helm repo update
```

2. clone the repo

```
git clone https://github.com/AhmedMojahed/elk-stack.git
cd elk-stack
```

3. deploy elasticsearch (this values file from here['https://logz.io/blog/deploying-the-elk-stack-on-kubernetes-with-helm/'])

```
helm install elasticsearch elastic/elasticsearch -f elastic-minikube-values.yaml
```

4. deploy kibana

```
helm install kibana elastic/kibana
```

5. deploy logstash

```
helm install logstash elastic/logstash -f logstash-values.yaml
```

6. deploy filebeat

```
helm install filebeat elastic/filebeat -f filebeat-values.yaml
```
