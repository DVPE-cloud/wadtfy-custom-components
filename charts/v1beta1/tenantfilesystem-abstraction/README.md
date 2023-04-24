# tenantfilesystem-abstraction

![Version: 0.0.5-v1beta1](https://img.shields.io/badge/Version-0.0.5--v1beta1-informational?style=flat-square)

Abstracted helm blueprint for Tenant EFS Filesystems

## Installation
Installs custom wadtfy tenantfilesystem-abstraction crossplane chart.

**Preconditions**:
* [Crossplane](https://crossplane.io) needs to be installed on Kubernetes.

### Add Helm repository

```shell
helm repo add wadtfy-custom-component https://dvpe-cloud.github.io/wadtfy-custom-components
helm repo update
```

## Install wadtfy tenantfilesystem-abstraction chart

```sh
helm install tenantfilesystem-abstraction . -f values.yaml
```

## Configuration

The following table lists the configurable parameters of the chart and its default values.

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| components.global.deletionPolicy | string | `""` |  |
| components.global.name | string | `""` |  |
| components.global.region | string | `""` |  |
| config.tenant.awsAccountId | string | `""` |  |
| providerConfig.aws | string | `""` |  |
| providerConfig.k8s | string | `""` |  |
| tags[0].tagKey | string | `"wadtfy.bmwgroup.net/component-name"` |  |
| tags[0].tagValue | string | `""` |  |
| tags[1].tagKey | string | `"wadtfy.bmwgroup.net/cluster-account-id"` |  |
| tags[1].tagValue | string | `""` |  |
| tags[2].tagKey | string | `"wadtfy.bmwgroup.net/product-name"` |  |
| tags[2].tagValue | string | `""` |  |
