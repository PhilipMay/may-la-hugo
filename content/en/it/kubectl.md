---
title: kubectl
---

## Links
- [overview of kubectl](https://kubernetes.io/docs/reference/kubectl/overview/)
- [kubectl Cheat Sheet](https://kubernetes.io/docs/reference/kubectl/cheatsheet/)
- [kubectl Commands](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands)
- [list of resource types](https://kubernetes.io/docs/reference/kubectl/overview/#resource-types)

## Display Resources
- all: `kubectl get all -A -o wide`
- custom resource definitions: `kubectl get crd`
- ingressroutes (custom resource definition from Traefik): `kubectl get ingressroutes -A`
- component statuses: `kubectl get cs`
- list Longhorn replica: `kubectl get replica -A`

## Create Resources
- expose deployment: `kubectl expose deploy <deployment_name> --port <port_number>` - [more](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#expose)

## Delete Resources
- delete all from namespace: `kubectl delete all --all -n <namespace>`

## Special Commands
- ececute bash on pod: `kubectl exec --stdin --tty <pod_name> -- /bin/bash`
- stop / start a pod: `kubectl scale --replicas=<0/1> <deployment_name>`
- schedule Pods on the control-plane: `kubectl taint nodes --all node-role.kubernetes.io/master-`
- write yaml for kubectl command to file: `kubectl <command> --dry-run=client -o yaml > <file>.yaml`
- convert config file to configmap: `kubectl create configmap <config_map_name> --from-file=<config_file_name> --dry-run=client -o yaml > <filename>.yaml`
