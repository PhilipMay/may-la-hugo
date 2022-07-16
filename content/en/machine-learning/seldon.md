---
title: Seldon
---

# Seldon
- Seldon <https://www.seldon.io/>
- GitHub <https://github.com/SeldonIO/seldon-core>
- Doc <https://docs.seldon.io/projects/seldon-core/en/latest/>
- Installation
  - Install Seldon Core: <https://docs.seldon.io/projects/seldon-core/en/latest/workflow/github-readme.html#install-seldon-core>
  - <https://github.com/SeldonIO/seldon-core/tree/master/examples/auth>
  - Videos: <https://docs.seldon.io/projects/seldon-core/en/latest/tutorials/videos.html>

## Install
- Use k8s `1.17.0`: `minikube start -p aged
  --kubernetes-version=v1.17.0`
  - current version line `1.18.x` does not work (at the moment)
  - when you want to start k8s again you have to provide this
    command again - with version number
  - maybe delete all k8s before: `minikube delete --all` - maybe
    with `--purge`
- follow this guide to install istio:
  <https://github.com/SeldonIO/seldon-core/tree/master/examples/auth>
  - let's use version 1.5 like the guide sais
  - `%%curl -L https://istio.io/downloadIstio | ISTIO_VERSION=1.5.0
    TARGET_ARCH=x86_64 sh - %%`
  - add `export PATH="$PATH:/home/mike/bin/istio-1.5.0/bin"` to
    `.bashrc`
  - `istioctl manifest apply --set profile=demo`
- install the rest
  - checkout seldon-core from git:
    <https://github.com/SeldonIO/seldon-core>
  - change to directory `examples/auth`
  - follow the rest of the guide:
    <https://github.com/SeldonIO/seldon-core/blob/master/examples/auth/README.md>
  - Uninstall: `helm uninstall seldon-core --namespace
    seldon-system`

## Using and Testing with Python
- Usage with Python:
  <https://docs.seldon.io/projects/seldon-core/en/v1.1.0/python/index.html>
  - Seldon Core Python Package:
    <https://docs.seldon.io/projects/seldon-core/en/v1.1.0/python/python_module.html>
  - Seldon Python Component:
    <https://docs.seldon.io/projects/seldon-core/en/v1.1.0/python/python_component.html>
  - Seldon Python Client:
    <https://docs.seldon.io/projects/seldon-core/en/v1.1.0/python/seldon_client.html>
  - Python API:
    <https://docs.seldon.io/projects/seldon-core/en/v1.1.0/python/api/modules.html>
  - Class name and script name have to be exactly the same!
- Testing - without Kubernetis - just localy
  - start API to test
    - `export PREDICTIVE_UNIT_PARAMETERS='[{"name":"model_uri","value":"<uri>","type":"STRING"}]'`
    - example: `export PREDICTIVE_UNIT_PARAMETERS='[{"name":"model_uri","value":"file:///home/myuser/models/german_sentiment_electra","type":"STRING"}]'`
  - get model from cloud storage: `model_file = os.path.join(seldon_core.Storage.download(self.model_uri))`
  - `seldon-core-microservice <script_name_without_.py> REST`
  - `curl -X POST -H 'Content-Type: application/json' -d '{"data": { "ndarray": ["data1", "data2"]}}' http://127.0.0.1:5000/api/v1.0/predictions`
- see here: <https://docs.seldon.io/projects/seldon-core/en/v0.3.0/workflow/api-testing.html>
  - *Alternatively, if your component is a Python module you can run it directly from python using the core tool `seldon-core-microservice`" [...]*
- Testing Your Model Endpoints: <https://docs.seldon.io/projects/seldon-core/en/v1.1.0/workflow/serving.html>
