# Deploying a full DSP using K8S

## Getting started
### AWS
https://docs.aws.amazon.com/eks/latest/userguide/getting-started.html

### GCP
https://cloud.google.com/kubernetes-engine/docs/quickstart

## Deployment using helm
### Install helm

Download client from: https://docs.helm.sh/using_helm/#installing-helm
#### Ubuntu
```
sudo snap install helm --classic
```

Run:
```
helm init
helm update repo

kubectl create serviceaccount --namespace kube-system tiller 
kubectl create clusterrolebinding tiller-cluster-rule --clusterrole=cluster-admin --serviceaccount=kube-system:tiller 
kubectl patch deploy --namespace kube-system tiller-deploy -p '{"spec":{"template":{"spec":{"serviceAccount":"tiller"}}}}'

```
### Setup dashboard
```
helm install stable/kubernetes-dashboard
```
### Install DAPP-DSP helm chart
```
wget https://.../charts/dapp-dsp-config.yaml
helm install -f dapp-dsp-config.yaml https://.../charts/dapp-dsp.tgz
```

