# OpenShift GitOps Demo

## Operator Setup

* Install GitOps Operator with `oc apply -f gitops-operator-install/subscription.yaml`
* Install Pipelines Operator with `oc apply -f pipelines-operator-install/subscription.yaml`

## KAM

* Download the kam cli tool (https://github.com/redhat-developer/kam) in the version related to your GitOps and Pipelines Version
* Bootstrap your git-ops repo
```
kam bootstrap \
  --service-repo-url https://github.com/marcoklaassen/taxi.git \
  --gitops-repo-url https://github.com/marcoklaassen/gitops-demo-1.4.3 \
  --git-host-access-token <get it from https://github.com/settings/tokens> \
  --image-repo quay.io/mklaasse/taxi \
  --dockercfgjson ~/Downloads/mklaasse-gitops-auth.json \
  --push-to-git=false
```
## Deployment of Infrastructure

* With `oc apply -k gitops/config/argocd` you can setup your argocd environment
* With `oc apply -f secrets` you are able to apply all the generated secrets
* Login to your ArgoCD UI with admin account. You can get the admin password with `oc get secret -n openshift-gitops openshift-gitops-cluster -o json | jq -r '.data."admin.password"' | base64 -d`

## Create GitHub Webhook with KAM CLI tool

The command

```
cd gitops && \
kam webhook create \
    --git-host-access-token <get it from https://github.com/settings/tokens> \
    --env-name dev \
    --service-name taxi
```

creates an already configured webhook for your in your application github repo.

just a change
