# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [2.6.0]

### Change

* Converted native Patch and Transform composition to function based P&T
* Removed external XR's and make it obsolete:
  * `xtenantfilesystem-mounttargets`
  * `xtenantfilesystem-env`

> [!IMPORTANT]
> Do not upgrade until all the following requirements are met !
>
> Requirements:
> * Crossplane 1.15 with enabled `function` support
> * Installed Crossplane Functions:
>   * function-patch-and-transform
>   * function-auto-ready
>   * function-environment-configs
>   * function-go-templating

## [2.5.3]

### Change

* Added missing AWS Policy permission `elasticfilesystem:DescribeAccessPoints` to fix access denied errors.

## [2.5.2]

### Change

* Set ReadinessCheck to none for `XTenantFileSystemEnv` XR Resource.

## [2.5.1]

### Change

* Removed the empty `env` composition to fulfill Crossplane 1.14 admission webhook requirements.

## [2.5.0]

### Add

* Implemented crossplane `Usage` resources in tenantfilesystem to avoid orphaned deletions
  * Crossplane >= 1.14 required
* Argocd TrackingID patch for StorageClasses (disabled in Composition Code at the moment)

## [2.4.0]
### Change

* CRD parameter `region` got deprecated. Will be removed in the next major version.

## [2.3.0]
### Change

* Fix `persistentVolume` remove if the `persistentVolumeClaim` gets deleted with `reclaimPolicy: delete`.
An AWS IAM policy permission right was missing.

## [2.2.0]
### Added

* Extended `efsThroughputMode` with `elastic` throughput mode.

## [2.1.1]
### Added

* TenantFilesystem parameter documentation

## [2.1.0]
### Changed

* Fix the availibility zone parameter set in StorageClass by getting the availibitlyZone value from one of the mounttargets 

## [2.0.0]
### Changed

* Add parameter `region` instead of reading it from TenantEnv

## [1.2.0]
### Fix

* Added missing `elasticfilesystem:TagResource` permissions in AWS Tenant Policy 

## [1.1.1]

### Fix

* ArgoCD diff detection with k8s-role-binding

## [1.1.0]

### Changed

* Renamed release reference from `tenantfilesystem-abstraction` to `tenantfilesystem-mounttargets`

## [1.0.0]

> NOTE: This is a breaking change which is not backwards compatible with previous versions of this component.

### Changed

* Mount Targets can now be added as a list which allows dynamically sized VPCs to be configured with a filesystem.

## [0.4.1]

### Changed

* Fixed issue with an empty ProviderConfig after upgrade of the Provider by using EnvironmentConfig 

## [0.4.0]

### Changed

* Used XTenant related EnvironmentConfig
* Add missing efs and storageClass Parameters
* Refactor filenames
* Improvements and fixes

## [0.3.0]

### Added

* XEnv XRD to patch EnvironmentConfig variables
* Use PatchSets
* Refactoring
* Improvements and fixes

## [0.2.0]

### Added

* Moved StorageClass secret into claim namespace
* WADTFY Tags
* Improvements and fixes

## [0.1.0]

### Added

* Initial Version

[2.6.0]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/tenant-filesystem-2.6.0-v1beta1/charts/v1beta1/tenantfilesystem
[2.5.3]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/tenant-filesystem-2.5.3-v1beta1/charts/v1beta1/tenantfilesystem
[2.5.2]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/tenant-filesystem-2.5.2-v1beta1/charts/v1beta1/tenantfilesystem
[2.5.1]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/tenant-filesystem-2.5.1-v1beta1/charts/v1beta1/tenantfilesystem
[2.5.0]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/tenant-filesystem-2.5.0-v1beta1/charts/v1beta1/tenantfilesystem
[2.4.0]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/tenant-filesystem-2.4.0-v1beta1/charts/v1beta1/tenantfilesystem
[2.3.0]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/tenant-filesystem-2.3.0-v1beta1/charts/v1beta1/tenantfilesystem
[2.2.0]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/tenant-filesystem-2.2.0-v1beta1/charts/v1beta1/tenantfilesystem
[2.1.1]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/tenant-filesystem-2.1.1-v1beta1/charts/v1beta1/tenantfilesystem
[2.1.0]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/tenant-filesystem-2.1.0-v1beta1/charts/v1beta1/tenantfilesystem
[2.0.0]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/tenant-filesystem-2.0.0-v1beta1/charts/v1beta1/tenantfilesystem
[1.2.0]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/tenant-filesystem-1.2.0-v1beta1/charts/v1beta1/tenantfilesystem
[1.1.1]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/tenant-filesystem-1.1.1-v1beta1/charts/v1beta1/tenantfilesystem
[1.1.0]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/tenant-filesystem-1.1.0-v1beta1/charts/v1beta1/tenantfilesystem
[1.0.0]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/tenant-filesystem-1.0.0-v1beta1/charts/v1beta1/tenantfilesystem
[0.4.1]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/tenant-filesystem-0.4.1-v1beta1/charts/v1beta1/tenantfilesystem
[0.4.0]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/tenant-filesystem-0.4.0-v1beta1/charts/v1beta1/tenantfilesystem
[0.3.0]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/tenantfilesystem-0.3.0/charts/tenantfilesystem
[0.2.0]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/tenantfilesystem-0.2.0/charts/tenantfilesystem
[0.1.0]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/charts/v1beta1/tenantfilesystem


