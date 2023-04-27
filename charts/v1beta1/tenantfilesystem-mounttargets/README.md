# tenantfilesystem-mounttargets

![Version: 0.2.0-v1beta1](https://img.shields.io/badge/Version-0.2.0--v1beta1-informational?style=flat-square)

Helm blueprint for Tenant Filesystem Mounttargets.

## Installation
Installs custom wadtfy tenantfilesystem-mounttargets crossplane chart.

**Preconditions**:
* [Crossplane](https://crossplane.io) needs to be installed on Kubernetes.

### Add Helm repository

```shell
helm repo add wadtfy-custom-component https://dvpe-cloud.github.io/wadtfy-custom-components
helm repo update
```

## Install wadtfy tenantfilesystem-mounttargets chart

```sh
helm install tenantfilesystem-mounttargets . -f values.yaml
```

## Configuration

The following table lists the configurable parameters of the chart and its default values.

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| components.global.deletionPolicy | string | `""` |  |
| components.global.name | string | `""` |  |
| components.global.region | string | `""` |  |
| components.mounttarget.fileSystemIDRef.name | string | `nil` |  |
| components.mounttarget.securityGroupRef.name | string | `nil` |  |
| components.mounttarget.subnetIds | string | `nil` |  |
| providerConfig.aws | string | `""` |  |
