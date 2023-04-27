# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.1.0]

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

[1.1.1]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/tenant-filesystem-1.1.1-v1beta1/charts/v1beta1/tenantfilesystem
[1.1.0]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/tenant-filesystem-1.1.0-v1beta1/charts/v1beta1/tenantfilesystem
[1.0.0]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/tenant-filesystem-1.0.0-v1beta1/charts/v1beta1/tenantfilesystem
[0.4.1]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/tenant-filesystem-0.4.1-v1beta1/charts/v1beta1/tenantfilesystem
[0.4.0]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/tenant-filesystem-0.4.0-v1beta1/charts/v1beta1/tenantfilesystem
[0.3.0]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/tenantfilesystem-0.3.0/charts/tenantfilesystem
[0.2.0]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/tenantfilesystem-0.2.0/charts/tenantfilesystem
[0.1.0]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/charts/v1beta1/tenantfilesystem


