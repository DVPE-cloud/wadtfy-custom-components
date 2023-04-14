# cm-abstraction

![Version: 0.1.1-v1beta1](https://img.shields.io/badge/Version-0.1.1--v1beta1-informational?style=flat-square)

Abstracted helm implementation for ConfigMap

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

## Configuration

The following table lists the configurable parameters of the chart and its default values.

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| data | string | `nil` |  |
| name | string | `nil` |  |
