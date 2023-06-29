# irsa

![Version: 1.1.0-v1beta1](https://img.shields.io/badge/Version-1.1.0--v1beta1-informational?style=flat-square)

Helm chart for installing a custom irsa crossplane xrd.

## Installation
Installs custom wadtfy IRSA (Iam Roles for ServiceAccounts) crossplane XRD on an existing Kubernetes cluster within a specific namespace.

**Preconditions**:
* [Crossplane](https://crossplane.io) needs to be installed on Kubernetes.

### Add Helm repository

```shell
helm repo add wadtfy-custom-component https://dvpe-cloud.github.io/wadtfy-custom-components
helm repo update
```

## Install wadtfy irsa chart

```sh
helm install irsa . -f values.yaml
```
