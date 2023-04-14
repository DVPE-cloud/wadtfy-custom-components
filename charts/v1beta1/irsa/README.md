# irsa

![Version: 0.1.0](https://img.shields.io/badge/Version-0.1.0-informational?style=flat-square)

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

## Configuration

The following table lists the configurable parameters of the chart and its default values.

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| provider.kubernetes | string | `nil` | The name of the Kubernetes Crossplane Provider used to provision this component. |
