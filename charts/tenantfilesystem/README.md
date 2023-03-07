# tenantfilesystem

![Version: 0.1.0](https://img.shields.io/badge/Version-0.1.0-informational?style=flat-square)

Helm Chart for installing a custom tenantfilesystem xrd

## Installation
Installs custom wadtfy tenantfilesystem crossplane XRD on an existing Kubernetes cluster for a specific namespace.

**Preconditions**:
* [Crossplane](https://crossplane.io) need to be installed on Kubernetes.
* The default [AWS Crossplane Provider](https://github.com/crossplane-contrib/provider-aws) is used for provisioning AWS Resources.

### Add Helm repository

```shell
helm repo add wadtfy-custom-component https://dvpe-cloud.github.io/wadtfy-custom-components
helm repo update
```

## Install wadtfy tenantfilesystem chart

```sh
helm install tenantfilesystem . -f values.yaml
```

## Use TenantFileSystemClaim to create Filesystems

Create a `tenantfilesystemclaim.yaml` and set the Tenant Account related values

Sample:

```yaml
apiVersion: apiextensions.crossplane.io/v1alpha1
kind: tenantfilesystemclaim
metadata:
  name: tenantname-filesystemname
  namespace: tenant-namespace
spec:
  compositionRef:
    name: tenantfilesystem
  # Tenant AWS Account ID
  tenantAccountID: ""
  # Crossplane ProviderConfig from Tenant
  tenantProviderConfig:
  # AWS VPC ID
  vpcId:
  # AWS VPC Subnet ID's
  vpcSubnetIdA:
  vpcSubnetIdB:
  vpcSubnetIdC:
  # AWS Account Region
  region:
  # EFS Performance Mode
  efsPerformanceMode:
  # EFS Throughput Mode
  efsThroughputMode:
  # StorageClass specific values
  storageClass:
    directoryPerms: "700"
    basePath: "/dynamic_provisioning"
  writeConnectionSecretToRef:
    name:
```

```sh
kubectl apply -f environment-sample.yaml
```

## Configuration

The following table lists the configurable parameters of the chart and its default values.

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| aws.accountId | string | `nil` | The AWS Account ID from EKS Cluster |
| aws.cidrIp | string | `nil` | The VPC CIDR IP Network from EKS Cluster |
| eks.csiDriverControllerSaRole | string | `nil` | The Kubernetes service account name which the `efs-csi-controller` Deployment is using |
| eks.csiDriverNodeSaRole | string | `nil` | The Kubernetes service account name which the `efs-csi-node` Daemonset is using |
