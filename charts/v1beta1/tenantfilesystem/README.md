# tenant-filesystem

![Version: 2.1.1-v1beta1](https://img.shields.io/badge/Version-2.1.1--v1beta1-informational?style=flat-square)

Helm Chart for installing a custom tenantfilesystem xrd

## Installation
Installs custom wadtfy tenantfilesystem crossplane XRD on an existing Kubernetes cluster for a specific namespace.

**Preconditions**:
* [Crossplane](https://crossplane.io) need to be installed on Kubernetes.
* The default [AWS Crossplane Provider](https://github.com/crossplane-contrib/provider-aws) is used for provisioning AWS Resources.
* AWS VPC Peering between the WADTFY Cluster account and the tenant account
* At least three AWS availability zones in the VPC are required to establish an EFS connectivity.

### Add Helm repository

```shell
helm repo add wadtfy-custom-component https://dvpe-cloud.github.io/wadtfy-custom-components
helm repo update
```

## Install wadtfy tenantfilesystem chart

```sh
helm install tenantfilesystem . -f values.yaml
```

After

## Use TenantFileSystem to create Filesystems

Create a `tenantfilesystem.yaml` and set the Tenant Account related values

Example:

```yaml
apiVersion: apiextensions.crossplane.io/v1alpha1
kind: tenantfilesystem
metadata:
  name: name
  namespace: namespace
spec:
  compositionRef:
    name: tenant-filesystem
  vpcId: AWS_ACCOUNT_ID
  # AWS VPC Subnet ID's
  subnetIds:
    - SubnetID1
    - SubnetID2
    :
  # EFS Performance Mode
  efsPerformanceMode: generalPurpose
  # EFS Throughput Mode
  efsThroughputMode: provisioned
  # EFS Provisioned Throughput (only capable with efsThroughputMode: provisioned)
  efsProvisionedThroughputInMibps: 200
  # StorageClass specific values
  storageClass:
    directoryPerms: "700"
    basePath: "/dynamic_provisioning"
```

```sh
kubectl apply -f tenantfilesystem.yaml
```

## Parameter Description

| Key | Type | Required | Description |
|-----|------|---------|-------------|
| deletionPolicy | enum: ["Orphan", "Delete"] | no | Set the crossplane deletion policy on all resources that will created. `Default: delete`. |
| vpcId | string | yes | ID of the VPC (Virtual Private Network) in that `vpcSubnetId's` are running. |
| subnetIds | array | yes | ID's of the Subnet's from the `vpcId` . At least one subnetId is required. |
| efsPerformanceMode | enum: ["generalPurpose", "maxIO"] | yes | The performance mode this EFS instance should operate in. |
| efsThroughputMode | enum: ["bursting", "provisioned"] | yes | Specifies the throughput mode for the file system, either bursting or provisioned. If you set ThroughputMode to provisioned, you must also set a value for ProvisionedThroughputInMibps. |
| efsProvisionedThroughputInMibps | integer | no | Set the Throughput in Mib/s. |
| storageClass | object | yes | - |
| storageClass.basePath | string | no | Path under which access points for dynamic provisioning is created. If this parameter is not specified, access points are created under the root directory of the file system. |
| storageClass.directoryPerms | string | no | Directory permissions for AWS EFS Access Point root directory creation. |
| storageClass.uid | string | no | POSIX user Id to be applied for Access Point root directory creation and for user identity enforcement. |
| storageClass.gid | string | no | POSIX group Id to be applied for Access Point root directory creation and for user identity enforcement. |
| storageClass.gidRangeStart | string | no | Start range of the POSIX group Id to be applied for Access Point root directory creation and for user identity enforcement. Not used if uid/gid is set. For user identity enforcement, this value will be applied as both the uid and the gid. |
| storageClass.gidRangeStop | string | no | End range of the POSIX group Id. Not used if uid/gid is set. |
| storageClass.reclaimPolicy | enum: ["Retain", "Delete"] | no | PersistentVolumes that are dynamically created by a StorageClass will have the reclaim policy specified in the reclaimPolicy field of the class, which can be either Delete or Retain. `Default: Delete`. |
| region | string | yes | Set the AWS Region where the EFS Filesystem should created. |

### Other Parameters

The XRD reads some other parameters that are store in a `EnvironmentConfig` Resource.
That `EnvironmentConfig` is provided and automatically created by the `XTenant` resource.

The `EnvironmentConfig` contains follow parameters.

| Key | Description |
|-----|-------------|
| awsAccountId | ID of the Tenant AWS Account |
| product | Name of the Deployment Product |
| providerConfig | The reference Name for AWS Access. This config is used by the crossplane composition to have access to the particular AWS Account. |

## Sources

[aws-efs-csi-driver](https://github.com/kubernetes-sigs/aws-efs-csi-driver)

[AWS EFS](https://docs.aws.amazon.com/efs/latest/ug/whatisefs.html)

## Configuration

The following table lists the configurable parameters of the chart and its default values.

