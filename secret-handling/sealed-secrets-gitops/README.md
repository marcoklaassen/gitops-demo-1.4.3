# Sealed Secrets with OpenShift and OpenShift GitOps

## Install kubeseal

* Download binary from `https://github.com/bitnami-labs/sealed-secrets/releases/download/v0.17.3/kubeseal-0.17.3-darwin-amd64.tar.gz`
* Add Binary to path


## Cluster Side controller

The cluster side controller will be deployed by our sealed secret argo app.
The controller is located in `base/02-controller/controller.yaml`.
