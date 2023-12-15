# tenant-filesystem

![Version: 2.5.2-v1beta1](https://img.shields.io/badge/Version-2.5.2--v1beta1-informational?style=flat-square)

Helm Chart for installing a custom tenantfilesystem xrd

# Tenantfilesystem

Helm Chart for installing a custom tenantfilesystem xrd

## Installation
Installs custom wadtfy tenantfilesystem crossplane XRD on an existing Kubernetes cluster for a specific namespace.

**Preconditions**:
* [Crossplane](https://crossplane.io) need to be installed on Kubernetes.
* The default [AWS Crossplane Provider](https://github.com/crossplane-contrib/provider-aws) is used for provisioning AWS Resources.
* AWS VPC Peering between the WADTFY Cluster account and the tenant account
* At least one AWS availability zone in the VPC are required to establish an EFS connectivity.
* OIDC Provider connection between both Accounts (WADTFY and Tenant) with CloudFormation

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

## Composed Resources created by the TenantFilesystem

| Resource | Purpose |
|----------|---------|
| TenantFileSystemEnv | To buffer EnvironmentConfig parameters. |
| IAM Role | It is an assume Role to give the ServiceAccount the access to create EFS Filesystem on Tenant AWS Account. |
| IAM Policy | Describe the permissions for the assume Role. |
| IAM PolicyAttach | Link the Role and Policy together. |
| SecurityGroup | Describe the IP Firewall rules to access the Tenant Filesystem Server IP addresses. |
| KMS Key | The Encryption Key for the EFS Filesystem. |
| Mounttargets | The EFS Server IP addresses. |
| Role | A Kubernetes Role thats allow the ServiceAccount which is used by the StorageClass to use the AWS IAM Role. |
| RoleBinding | Kubernete Resource that link the Role and ServiceAccount together. |
| Secret | This Secrets contains the AWS Account that will be used by the StorageClass. |
| EFS FileSystem | AWS EFS Filesystem it self. |
| StorageClass | Provided StorageClass to use from the Tenant for PV's/PVC's |
| Usages | Crossplane Resource that prevent deletion of Resources that are still in used to protect the deletion-chain |

## Parameter Description

| Key | Type | Required | Description |
|-----|------|----------|-------------|
| deletionPolicy | enum: ["Orphan", "Delete"] | no | Set the crossplane deletion policy on all resources that will be created. `Default: delete`. |
| vpcId | string | yes | ID of the VPC (Virtual Private Network) in which `vpcSubnetId's` are running. |
| subnetIds | array | yes | ID's of the Subnet's from the `vpcId`. At least two subnetIds should be used due to availability reasons. |
| efsPerformanceMode | enum: ["generalPurpose", "maxIO"] | yes | The performance mode this EFS instance should operate in. See [EFS Performance](https://docs.aws.amazon.com/efs/latest/ug/performance.html) for details. |
| efsThroughputMode | enum: ["bursting", "provisioned", "elastic"] | yes | Specifies the throughput mode for the file system, either bursting or provisioned. If you set ThroughputMode to provisioned, you must also set a value for ProvisionedThroughputInMibps. See [EFS Throughput Modes|](https://docs.aws.amazon.com/efs/latest/ug/performance.html#throughput-modes) for details. |
| efsProvisionedThroughputInMibps | integer | no | Set the Throughput in Mib/s. |
| storageClass | object | yes | - |
| storageClass.basePath | string | no | Path under which access points for dynamic provisioning is created. If this parameter is not specified, access points are created under the root directory of the file system. |
| storageClass.directoryPerms | string | no | Directory permissions for AWS EFS Access Point root directory creation. |
| storageClass.uid | string | no | POSIX user Id to be applied for Access Point root directory creation and for user identity enforcement. |
| storageClass.gid | string | no | POSIX group Id to be applied for Access Point root directory creation and for user identity enforcement. |
| storageClass.gidRangeStart | string | no | Start range of the POSIX group Id to be applied for Access Point root directory creation and for user identity enforcement. Not used if uid/gid is set. For user identity enforcement, this value will be applied as both the uid and the gid. |
| storageClass.gidRangeStop | string | no | End range of the POSIX group Id. Not used if uid/gid is set. |
| storageClass.reclaimPolicy | enum: ["Retain", "Delete"] | no | PersistentVolumes that are dynamically created by a StorageClass will have the reclaim policy specified in the reclaimPolicy field of the class, which can be either Delete or Retain. `Default: Delete`. |

### Other Parameters

The XRD reads some other parameters that are stored in an `EnvironmentConfig` Resource.
This `EnvironmentConfig` is provided and automatically created by the `XTenant` resource and is only listed here for the sake of completeness.

The `EnvironmentConfig` contains the following parameters.

| Key | Description |
|-----|-------------|
| awsAccountId | ID of the Tenant AWS Account |
| product | Name of the Deployment Product |
| providerConfig | The name of the Crossplane `ProviderConfig` allowing Crossplane access to a particular AWS Account. |

## Sources

[aws-efs-csi-driver](https://github.com/kubernetes-sigs/aws-efs-csi-driver)

[AWS EFS](https://docs.aws.amazon.com/efs/latest/ug/whatisefs.html)

## Configuration

The following table lists the configurable parameters of the chart and its default values.

## Limitations

### EFS access across AWS regions

The current AWS CSI Driver does not support region configuration injection per StorageClass or PVCs.
Therefor it is not possible to mount an remote EFS that does not match with the region from the WADTFY Kubernetes cluster.
Example: If the WADTFY Cluster runs in eu-west the tenantfilesystem cannot be created in other regions but in eu-west.

