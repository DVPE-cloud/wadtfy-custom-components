# tenant

![Version: 3.0.0-v1beta1](https://img.shields.io/badge/Version-3.0.0--v1beta1-informational?style=flat-square)

Helm chart for installing a custom tenant crossplane xrd.

## Installation
Installs custom wadtfy tenant crossplane XRD on an existing Kubernetes cluster for a specific namespace.

**Preconditions**:
* [Crossplane](https://crossplane.io) and [External-Secrets](https://external-secrets.io/v0.7.2/) need to be installed on Kubernetes.
* The default [AWS Crossplane Provider](https://github.com/crossplane-contrib/provider-aws) is used for provisioning AWS Resources.

### Add Helm repository

```shell
helm repo add wadtfy-custom-component https://dvpe-cloud.github.io/wadtfy-custom-components
helm repo update
```

## Install wadtfy tenant chart

```sh
helm install tenant . -f values.yaml
```
