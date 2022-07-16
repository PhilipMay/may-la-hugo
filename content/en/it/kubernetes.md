---
title: Kubernetes
---

## Links
- Kubernetes: <https://kubernetes.io/>
  - Deployments: <https://kubernetes.io/docs/concepts/workloads/controllers/deployment/>
- kubectl
  - Doc: <https://kubernetes.io/docs/reference/kubectl/overview/>
  - Install and Set Up kubectl:
    <https://kubernetes.io/docs/tasks/tools/install-kubectl/>
- minikube
  - Doc: <https://minikube.sigs.k8s.io/>
  - GitHub: <https://github.com/kubernetes/minikube>

## Commands
- Minikube commands: <https://minikube.sigs.k8s.io/docs/commands/>
  - [Start local
    Kubernetes](https://minikube.sigs.k8s.io/docs/commands/start/):
    `minikube start`
  - [Stop local Kubernetes
    cluster](https://minikube.sigs.k8s.io/docs/commands/stop/):
    `minikube stop`
  - [Get status of local
    Kubernetes](https://minikube.sigs.k8s.io/docs/commands/status/):
    `minikube status`
  - Start old version (`1.15.0 for example`): `minikube start -p
    aged --kubernetes-version=v1.15.0`
  - list services: `minikube service list`
  - get Kubernetes URL for a service: `minikube service
    <resource_name>`
  - start the dashboard: `minikube dashboard`
  - get minikube version: `minikube version`
- kubectl Commands:
  <https://kubernetes.io/docs/reference/kubectl/overview/>
  - get info about the cluster: `kubectl cluster-info`
  - Get version of k8s: `kubectl version`
  - display all pods across all namespaces: `kubectl get pods -A`
  - display state of resource: `kubectl describe service
    <resource_name>`
  - display infos of resource: `kubectl get services
    <resource_name>`
  - delete deployment: `kubectl delete deployment <deployment_name>`
  - namespace commands
    - List namespaces: `kubectl get namespace`
    - Create namespace: `kubectl create namespace
      <namespace_name>`

## Installation
- install Minikube: <https://minikube.sigs.k8s.io/docs/start/>
- install KVM: <https://help.ubuntu.com/community/KVM/Installation>

First starts looks like this:
```text
$ minikube start
😄  minikube v1.13.0 on Ubuntu 18.04
✨  Automatically selected the kvm2 driver
💾  Downloading driver docker-machine-driver-kvm2:
    > docker-machine-driver-kvm2.sha256: 65 B / 65 B [-------] 100.00% ? p/s 0s
    > docker-machine-driver-kvm2: 13.81 MiB / 13.81 MiB  100.00% 1.13 MiB p/s 1
💿  Downloading VM boot image ...
    > minikube-v1.13.0.iso.sha256: 65 B / 65 B [-------------] 100.00% ? p/s 0s
    > minikube-v1.13.0.iso: 173.73 MiB / 173.73 MiB  100.00% 1.61 MiB p/s 1m48s
👍  Starting control plane node minikube in cluster minikube
💾  Downloading Kubernetes v1.19.0 preload ...
    > preloaded-images-k8s-v6-v1.19.0-docker-overlay2-amd64.tar.lz4: 486.28 MiB
🔥  Creating kvm2 VM (CPUs=2, Memory=2200MB, Disk=20000MB) ...
🐳  Preparing Kubernetes v1.19.0 on Docker 19.03.12 ...
🔎  Verifying Kubernetes components...
🌟  Enabled addons: default-storageclass, storage-provisioner
💡  kubectl not found. If you need it, try: 'minikube kubectl -- get pods -A'
🏄  Done! kubectl is now configured to use "minikube" by default
```

## Helm
The package manager for Kubernetes
- <https://helm.sh/>
- Install: <https://docs.helm.sh/docs/intro/install/>
- Commands
  - add a chart repository (example): `$ helm repo add stable
    https://kubernetes-charts.storage.googleapis.com/`
  - list the charts you can install: `helm search repo stable`

If install fails with `Error: cannot re-use a name that is still in use`
the `--replace` flag can be used.

## Post Setup Examples
After setup:
```text
$ kubectl get pods -A
NAMESPACE              NAME                                        READY   STATUS    RESTARTS   AGE
kube-system            coredns-f9fd979d6-r2vhj                     1/1     Running   2          3h49m
kube-system            etcd-minikube                               1/1     Running   2          3h49m
kube-system            kube-apiserver-minikube                     1/1     Running   2          3h49m
kube-system            kube-controller-manager-minikube            1/1     Running   2          3h49m
kube-system            kube-proxy-tnk8g                            1/1     Running   2          3h49m
kube-system            kube-scheduler-minikube                     1/1     Running   2          3h49m
kube-system            storage-provisioner                         1/1     Running   5          3h49m
kubernetes-dashboard   dashboard-metrics-scraper-c95fcf479-b92v2   1/1     Running   2          3h45m
kubernetes-dashboard   kubernetes-dashboard-5c448bc4bf-tttfg       1/1     Running   2          3h45m
```
