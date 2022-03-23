# Sealed Secrets with OpenShift and OpenShift GitOps

## Install kubeseal

* Download binary from `https://github.com/bitnami-labs/sealed-secrets/releases/download/v0.17.3/kubeseal-0.17.3-darwin-amd64.tar.gz`
* Add Binary to path


## Cluster Side controller

First apply the CustomResourceDefinition `SealedSecret` to your OpenShift.


The cluster side controller will be deployed by our sealed secret argo app.
The controller is located in `base/02-controller/controller.yaml`.

Create your decrypted secret and encrypt this Secret with

`kubeseal --controller-namespace sealed-secrets --format yaml <secret-handling/sealed-secrets-gitops/base/03-secret/decrypted-foo-secret.yaml >secret-handling/sealed-secrets-gitops/base/03-secret/foo-secret.yaml`


Commit the new `foo-secret.yaml` to your git and push it. After ArgoCD has refreshed the sealed-secrets app, your sealed-secret will be applied.
